# PalletCloud Project Documentation & ADRs

**Centralized repository for PalletCloud's comprehensive project documentation, system architecture, and Architectural Decision Records (ADRs).**

PalletCloud is a sophisticated logistics and storage management platform designed to streamline pallet storage operations, booking workflows, and administrative processes. This repository serves as the single source of truth for all architectural decisions, system designs, and technical documentation.

---

## 📁 Repository Structure

### 📚 Documentation (`/docs`)
- **[System Requirements](docs/system-requirements.md)** - Comprehensive requirements specification including functional, technical, and business requirements
- **[High-Level Architecture](docs/high-level-architecture.md)** - System architecture overview with microservices design patterns
- **[Cloud Routing](docs/cloud-routing.md)** - Domain routing, proxy layer, and ingress configuration for pallet.omniphics.com
- **[User Journey & Order Status](docs/user-jouney-order-status.md)** - Complete user workflow and booking lifecycle documentation
- **[Service-Side User Creation Flow](docs/service-side-user-creation-flow.md)** - Backend user registration and onboarding processes
- **[Service-Side Partner Creation](docs/service-side-partner-creation.md)** - Partner onboarding and management workflows

### 🎨 Visual Diagrams (`/diagrams`)

#### System Architecture Diagrams
- **System Design High-Level Architecture** - Visual representation of the microservices architecture
- **System Design Cloud Routing** - Infrastructure and domain routing configuration diagram
- **User Service Schema ERD** - Entity Relationship Diagram for user service database design

#### Process Flow Diagrams
- **System Design User Journey** - User workflow and booking process visualization
- **System Design User Register Login Sequence** - Authentication and registration flow sequence diagram
- **System Design Booking Service Data Flow Sequence** - Booking service workflow and data flow
- **Service-Side Customer Creation Flow** - Backend customer onboarding process
- **Service-Side Partner Creation Flow** - Partner registration and setup workflow

#### Requirements & Planning
- **System Requirements Platform Mindmap** - Mind map of platform requirements and features
- **Source Files** (`/diagrams/_source`) - Editable diagram source files (DrawIO format)

### 🏛️ Architectural Decision Records (`/adrs`)
- **[Choosing MySQL over PostgreSQL](adrs/choosing-mysql-over-postgres.md)** - Database selection rationale
- **[Choosing Next.js 15 with React 18](adrs/choosing-next15-with-react18.md)** - Frontend framework decision
- **[Keycloak Integration Strategy](adrs/keycloak-integration-stratagy.md)** - Authentication and identity management approach
- **[Organization per Customer Architecture](adrs/organization-per-customer-architucture.md)** - Multi-tenancy design pattern
- **[Role Type Classification System](adrs/role-type-classification-system.md)** - User role and permission structure
- **[User Service Schema](adrs/user-service-schema.md)** - User service database design decisions

### 📄 Additional Resources (`/pdfs`)
- **System Requirements Platform Ideas** - Extended brainstorming and ideation documentation

### 📋 ADR Framework
- **[000-template.md](000-template.md)** - Standard template for Architectural Decision Records

---

## 🎯 Project Overview

PalletCloud is a comprehensive logistics and storage management platform that revolutionizes how businesses handle pallet storage, tracking, and operational workflows.

### 🚀 Core Capabilities

#### Customer Experience
- **Intelligent Storage Search** - Advanced filtering and availability checking
- **Seamless Booking System** - Real-time reservation and confirmation
- **Payment Processing & Verification** - Receipt upload and administrative verification workflow
- **Order Tracking** - Real-time status updates and notifications
- **Document Management** - Secure file handling and verification workflows

#### Operational Management
- **Check-in/Check-out Processes** - Streamlined pallet handling workflows
- **Inventory Tracking** - Real-time location and status monitoring
- **Partner Management** - Comprehensive partner onboarding and management
- **Activity Monitoring** - Comprehensive audit trails and system monitoring

#### Administrative Features
- **User Management** - Role-based access control with granular permissions
- **Multi-tenant Architecture** - Organization-per-customer isolation
- **Communication & Notifications** - Automated status updates and alerts
- **Reporting & Analytics** - Business intelligence and operational insights

### 🏗️ Architecture Highlights

#### Infrastructure & Deployment
- **Cloud-Native Architecture** with Cloudflare routing, proxy layer, and ingress configuration
- **Domain-based Service Routing** across www, admin, api, and auth subdomains (pallet.omniphics.com)
- **Containerized Microservices** with Kubernetes orchestration
- **High Availability** with multi-region deployment capabilities

#### Backend Services
- **Microservices Architecture** with dedicated services for Users, Bookings, Files, Notifications, and Activity tracking
- **API Gateway** for centralized routing, security, and rate limiting
- **Event-driven Architecture** for real-time updates and system integration
- **Database per Service** pattern with MySQL as primary database

#### Authentication & Security
- **Centralized Authentication** with Keycloak integration
- **Role-based Access Control (RBAC)** with fine-grained permissions
- **Organization-level Isolation** for multi-tenant security
- **OAuth 2.0 / OpenID Connect** standard compliance

#### Frontend Applications
- **Next.js 15 with React 18** for modern, performant user interfaces
- **Responsive Design** optimized for desktop and mobile devices
- **Progressive Web App (PWA)** capabilities for enhanced user experience
- **Real-time Updates** with WebSocket integration

---

## 🚀 Getting Started

This repository serves as the central documentation hub for PalletCloud. Navigate through the documentation to understand:

### 📖 Documentation Journey
1. **[System Requirements](docs/system-requirements.md)** - Start here to understand what the platform accomplishes
2. **[High-Level Architecture](docs/high-level-architecture.md)** - Learn how the system is structured and organized
3. **[Cloud Routing](docs/cloud-routing.md)** - Understand the infrastructure setup and domain configuration
4. **[User Journey](docs/user-jouney-order-status.md)** - Follow how users interact with the platform
5. **[Service Flows](docs/service-side-user-creation-flow.md)** - Dive into backend processes and workflows

### 🎨 Visual Learning
- Explore the `/diagrams` directory for comprehensive visual representations
- Start with system architecture diagrams for high-level understanding
- Review process flows for detailed workflow comprehension
- Check ERD diagrams for database design insights

### 🏛️ Architectural Decisions
- Browse `/adrs` directory to understand key technical decisions
- Each ADR provides context, rationale, and consequences of architectural choices
- Follow the decision trail from database selection to framework choices

---

## 📋 ADR Framework

Our architectural decisions are documented using the ADR (Architectural Decision Record) framework to ensure transparency, traceability, and alignment across teams.

### 📝 ADR Process
- **Template**: Each ADR follows the standard template in `000-template.md`
- **Storage**: All ADRs are stored in the `/adrs` directory with descriptive filenames
- **Content**: ADRs capture context, decisions, consequences, and alternatives considered
- **Versioning**: ADRs are immutable; superseding decisions create new ADRs

### 🎯 Current ADRs
Our existing ADRs cover critical architectural decisions including:
- Database technology selection and rationale
- Frontend framework and version choices
- Authentication and identity management strategy
- Multi-tenancy and organization design patterns
- User role and permission system architecture
- Service schema and data modeling decisions

---

## 🔄 Project Status

**Current Phase**: **Architecture & Development** 

✅ **Completed**
- Comprehensive requirements gathering and analysis
- System architecture design and documentation
- Core ADRs for foundational technology decisions
- Database schema design and ERD creation
- User journey mapping and process flows
- Infrastructure and routing configuration

🚧 **In Progress**
- Detailed service specifications and API design
- Implementation planning and development roadmap
- Security and compliance framework development

📋 **Upcoming**
- Development environment setup and CI/CD pipeline
- Core service implementation and testing
- Integration testing and quality assurance
- Production deployment and monitoring setup

---

## 🤝 Contributing

This repository follows structured documentation practices:

- **Documentation Updates**: Follow markdown best practices and maintain consistency
- **ADR Creation**: Use the provided template for all architectural decisions
- **Diagram Updates**: Keep source files in `/diagrams/_source` for editability
- **Version Control**: All changes should be tracked and reviewed

---

## 📞 Support & Contact

For questions about the architecture, decisions, or documentation:
- Review existing ADRs for architectural context
- Check documentation for detailed explanations
- Refer to diagrams for visual understanding

---

*This documentation is maintained as a living resource and evolves with the PalletCloud platform development.*