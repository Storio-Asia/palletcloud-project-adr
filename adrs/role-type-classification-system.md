# ADR-002: Role Type Classification System

## Status
Accepted

## Context
PalletCloud requires a flexible role-based access control (RBAC) system that can efficiently manage permissions across different categories of users. The platform serves multiple distinct user groups (customers, partners, system administrators) with vastly different permission requirements and operational contexts. A flat role structure would become unwieldy and difficult to maintain as the platform scales.

## Problem Statement
Without role categorization, we face several challenges:
- **Role Explosion**: Hundreds of granular roles without clear organization
- **Assignment Complexity**: Difficulty determining which roles apply to which user types
- **Maintenance Burden**: No clear pattern for role creation and management
- **Security Risks**: Accidental assignment of inappropriate roles to users
- **Query Performance**: Inefficient role lookups across all users

## Decision

### Role Type Classification
**Decision**: Introduce a `type` field in the Roles table to categorize roles into distinct types: `CUSTOMER`, `PARTNER`, and `SYSTEM`.

### Role Type Definitions

#### 1. CUSTOMER Type Roles
**Purpose**: Roles for individual users who consume storage services

**Characteristics**:
- Limited to booking and personal account management
- No administrative capabilities
- Self-service oriented permissions

#### 2. PARTNER Type Roles  
**Purpose**: Roles for business partners who provide storage services or have commercial relationships

**Characteristics**:
- Business-focused permissions
- Multi-user organization support
- Revenue and facility management capabilities

#### 3. SYSTEM Type Roles
**Purpose**: Platform administration and system management roles

**Characteristics**:
- Cross-organizational access capabilities
- Platform-wide administrative functions
- System configuration and monitoring


### Assignment Rules
- **CUSTOMER users** → Can only be assigned CUSTOMER type roles
- **PARTNER users** → Can only be assigned PARTNER type roles  
- **ADMIN users** → Can be assigned SYSTEM type roles

## Benefits

### 1. Efficient Role Management
**Query Optimization**:
```sql
-- Fast role lookup for user type
SELECT r.* FROM roles r WHERE r.type = 'CUSTOMER';

-- Efficient assignment validation
SELECT r.* FROM roles r 
WHERE r.type IN (SELECT allowed_role_types FROM user_type_permissions WHERE user_type = 'PARTNER');
```

### 2. Security Boundaries
- **Type-based Validation**: Prevent assigning system roles to customers
- **Clear Separation**: Business roles separated from system administration
- **Audit Trail**: Easy to track role assignments by category

### 3. Scalability
- **Organized Growth**: New roles added within clear categories
- **Maintainable Structure**: Role hierarchy remains comprehensible
- **Performance**: Indexed queries by role type

### 4. Developer Experience  
- **Clear Intent**: Role purpose immediately apparent from type
- **Easier Testing**: Roles can be tested in isolation by type
- **Documentation**: Self-documenting role structure

### Role Creation Guidelines
- **CUSTOMER roles**: Focus on self-service capabilities
- **PARTNER roles**: Business and operational permissions within organization
- **SYSTEM roles**: Platform administration, cross-organizational access

## Consequences

### Positive
- **Improved Security**: Type-based role assignment prevents privilege escalation
- **Better Organization**: Logical grouping of roles reduces complexity
- **Enhanced Performance**: Indexed role type queries improve response times
- **Simplified Management**: Role administration becomes more intuitive
- **Scalable Architecture**: Framework supports platform growth

### Negative
- **Initial Migration Effort**: Existing roles need classification and validation
- **Additional Complexity**: One more dimension to consider in role design
- **Learning Curve**: Team needs to understand type-based role model
