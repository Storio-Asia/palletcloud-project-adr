# PalletCloud Project Documentation & ADRs

**Centralized repository for PalletCloud's project documentation and Architectural Decision Records (ADRs).**

This repository contains comprehensive documentation for the PalletCloud logistics and storage management platform, including system requirements, architecture documentation, user journey mapping, and a framework for capturing architectural decisions.

## 📁 Repository Structure

### Documentation (`/docs`)
- **[System Requirements](docs/system-requirements.md)** - Comprehensive requirements specification including functional, technical, and business requirements
- **[High-Level Architecture](docs/high-level-architecture.md)** - System architecture overview with microservices design
- **[Cloud Routing](docs/cloud-routing.md)** - Domain routing, proxy layer, and ingress configuration for pallet.omniphics.com
- **[User Journey & Order Status](docs/user-jouney-order-status.md)** - Complete user workflow and booking lifecycle documentation

### Visual Diagrams (`/diagrams`)
- **System Design High-Level Architecture** - Visual representation of the microservices architecture
- **System Design Cloud Routing** - Infrastructure and domain routing configuration diagram
- **System Design User Journey** - User workflow and booking process visualization  
- **System Requirements Platform Mindmap** - Mind map of platform requirements and features
- **Source Files** (`/diagrams/_source`) - Editable diagram source files (DrawIO format)

### Additional Resources (`/pdfs`)
- **System Requirements Platform Ideas** - Extended brainstorming and ideation documentation

### ADR Framework
- **[000-template.md](000-template.md)** - Standard template for Architectural Decision Records
- **`/adrs`** - Directory for future architectural decision records

## 🎯 Project Overview

PalletCloud is a comprehensive logistics and storage management platform that provides:

### Core Capabilities
- **Storage Booking System** - Search, reserve, and manage storage spaces
- **Payment Processing & Verification** - Receipt upload and administrative verification workflow
- **Operational Management** - Check-in/check-out processes and inventory tracking
- **User Management** - Role-based access for customers and administrators
- **Communication & Notifications** - Automated status updates and alerts
- **Document Management** - Secure file handling and verification workflows
- **Activity Monitoring** - Comprehensive audit trails and system monitoring

### Architecture Highlights
- **Microservices Architecture** with dedicated services for Users, Bookings, Files, Notifications, and Activity tracking
- **API Gateway** for centralized routing and security
- **Cloud Infrastructure** with Cloudflare routing, proxy layer, and ingress configuration
- **Domain-based Service Routing** across www, admin, api, and auth subdomains
- **Centralized Authentication** server with Keycloak
- **Comprehensive workflow support** from search to completion
- **Administrative oversight** with verification workflows

## 🚀 Getting Started

This repository serves as the central documentation hub for PalletCloud. Use the documents above to understand:

1. **System Requirements** - What the platform needs to accomplish
2. **Architecture Design** - How the system is structured 
3. **Cloud Routing** - Infrastructure setup and domain routing configuration
4. **User Journey** - How users interact with the platform
5. **Visual Diagrams** - Architectural and workflow visualizations

## 📋 ADR Framework

Future architectural decisions will be documented using the ADR (Architectural Decision Record) framework:

- Each ADR follows the standard template in `000-template.md`
- ADRs will be stored in the `/adrs` directory
- ADRs capture context, decisions, consequences, and alternatives considered
- This ensures transparency, traceability, and alignment across teams

## 🔄 Status

This project is currently in the **documentation and design phase**, with comprehensive requirements gathering and architectural planning completed. The documentation provides the foundation for development of the PalletCloud platform.
