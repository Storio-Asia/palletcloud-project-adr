# Partner Creation Flow

![Partner Creation Flow](../diagrams/service-side-partner-creation-flow.png)

### Partner Journey Flow

1. **Partner Registration Request**

   * `POST /api/partners/register` from `AdminPortal`.
   * Payload includes:

     * **Organization Data** (name, description).
     * **Partner Profile Data** (company details, registration, address, industry, capacity, etc.).
     * **Primary User Data** (firstName, lastName, email, phone, type=`PARTNER`).

2. **Begin Database Transaction**

   * `UserService` initiates a transaction.

3. **Organization Creation**

   * `INSERT INTO Organization` with organizationId, name, description.
   * Returns `organizationId` (e.g., `org-abc-storage-123`).

4. **Organization Profile Creation**

   * `INSERT INTO Organization_Profile` with extended business details linked to `organizationId`.
   * Marks `isVerified=false` by default.
   * Returns `organizationProfileId`.

5. **User Creation**

   * `INSERT INTO User` for primary partner admin.
   * Fields: userId, organizationId, firstName, lastName, email, phone, type=`PARTNER`, status=`ACTIVE`.

6. **Role Assignment**

   * Query: `SELECT id FROM Roles WHERE type='PARTNER' AND name='PARTNER Admin'`.
   * Assign via `INSERT INTO User_Associated_Roles`.

7. **Commit Transaction**

   * Once organization, profile, user, and roles are persisted, transaction commits.

8. **Create Primary Company in Booking Service**

   * Calls `ServiceDiscovery` for `BookingService` URL.
   * `POST /api/companies/create-primary` with organization + profile details.
   * BookingService creates a **Primary Company** record linked to the partner.

9. **Success Response**

   * Returns:

     * `organizationId`, `userId`, `organizationProfileId`, `companyId`.
   * Message: **“Partner registration completed.”**

---

### Partner Alternative Flow – Adding Additional Users

1. **Add User Request**

   * `POST /api/partners/add-user` from `AdminPortal`.
   * Payload includes: `organizationId`, user details.

2. **Validation**

   * `SELECT * FROM Organization WHERE organizationId=?` to verify org exists.

3. **User Creation**

   * `INSERT INTO User` with type=`PARTNER`.
   * Status=`ACTIVE`.

4. **Role Assignment**

   * Query: `SELECT id FROM Roles WHERE type='PARTNER' AND name='PARTNER Staff'`.
   * Assign via `INSERT INTO User_Associated_Roles`.

5. **Success Response**

   * Returns new `userId`.
   * Message: **“Additional user created for partner.”**

---

### Partner Status Sequence

* **Pending** → Registration started.
* **Organization Created** → Organization inserted.
* **Organization Profile Created** → Extended profile added.
* **Primary User Active** → Admin user created and role assigned.
* **Company Created** → Booking Service company record established.
* **Additional Users Added** → Partner staff created.
* **Suspended** → Partner temporarily blocked.
* **Deleted** → Partner soft-deleted with related users.
