# EazyOps API Documentation

## Overview

Welcome to the EazyOps API! Our API provides programmatic access to your cloud cost and resource data, enabling you to automate cost optimization workflows, build custom reports, and integrate EazyOps with your existing tools.

This document covers:

- [List available organisations and users](list_organisations_users.md)
### User Authentication

- [List available organisations and users](list_organisations_users.md)
- [User Authentication](authentication.md)
- [Connected Clouds API](connected_clouds.md)
- [Available Connectors API](connected_clouds_connectors.md)
- [Overview API](overview_api.md)
- [Resource Listing API](resource_listing_api.md)
- [Reports API](reports.md)

**All endpoints require HTTPS and JSON payloads.**

---

## Getting Started

The EazyOps API is designed to be simple and intuitive. Here's a typical workflow:

1.  **Authenticate:** Obtain an authentication token to access the API.
2.  **Explore:** Discover your connected clouds and available connectors.
3.  **Analyze:** Get an overview of your organization's cloud resources and costs.
4.  **Optimize:** Identify cost-saving opportunities by listing resources and generating detailed reports.

## Authentication Flow Summary
1.  **Generate a temporary token:** `POST /api/v1/users`
2.  **Exchange the temporary token for an authentication token:** `GET /api/v1/users/login`
3.  **Access the API:** Use the authentication token in the `Authorization` header of your API requests.