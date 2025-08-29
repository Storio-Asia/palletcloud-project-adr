##  Keycloak Integration Strategy

- Status: Accepted
- Date: 2024-12-28
- Context: Authentication and User Management
- Decision: Hybrid Keycloak Integration
- Consequences: Flexible User Creation Patterns

### Context

The system needs to integrate with Keycloak for authentication while supporting different user creation workflows. We need to handle both direct user registration through Keycloak and programmatic user creation through our services.

Requirements:
- Support user self-registration through Keycloak interface
- Enable programmatic user creation for partner onboarding
- Maintain consistency between Keycloak and internal user data
- Handle profile completion workflows

### Decision

We implement a hybrid Keycloak integration strategy with two distinct user creation patterns:

1. **Direct Keycloak Registration**: Users can register directly through Keycloak interface
2. **Service-Managed Creation**: Services can create users programmatically in Keycloak

Key implementation details:
- Keycloak handles all authentication and basic user management
- Profile completion is mandatory after Keycloak user creation
- Services interact with Keycloak API for programmatic user creation
- User profiles are stored separately in our database, linked to Keycloak users

### Consequences

#### Positive
- **Flexible Registration**: Supports both self-service and managed user creation
- **Centralized Authentication**: All authentication handled by Keycloak
- **Service Integration**: Easy programmatic user management for business processes
- **Profile Separation**: Can extend user profiles without Keycloak limitations
- **Scalable**: Keycloak handles auth scaling concerns

#### Negative
- **Dual Management**: Must keep Keycloak and internal profiles synchronized
- **Complexity**: Two different user creation flows to maintain
- **Dependency**: Strong dependency on Keycloak availability
- **Data Consistency**: Risk of data inconsistency between systems

---