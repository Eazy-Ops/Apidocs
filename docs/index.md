

# EazyOps API Documentation

## Overview

The EazyOps API provides programmatic access to user authentication, organization/project/resource cost reports, and strategic recommendations for cloud cost optimization.

This document covers:

- [User Authentication](authentication.md)
- [Connected Clouds API](connected_clouds.md)
- [Available Connectors API](connected_clouds_connectors.md)
- [Overview API](overview_api.md)
- [Resource Listing API](resource_listing_api.md)
- [Reports API](reports.md)

**All endpoints require HTTPS and JSON payloads.**

---

## Authentication Flow Summary
1.  Generate token for user email → `POST /api/v1/users`
2.  Login with token → `GET /api/v1/users/login` → receive final Bearer token
3.  Access reports → `GET /api/reports/{type}/{id}` using Bearer token
