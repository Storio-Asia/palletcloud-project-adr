# Asynchronous Facility Search with Job Queue

## Status

Accepted

## Context
The existing facility search functionality was experiencing performance issues due to:

1. **Complex Search Operations**: Location-based searches with distance calculations using Haversine formula
2. **Slot Availability Checks**: Multiple database queries to check availability across date ranges
3. **Timeout Issues**: Complex searches taking 30-60+ seconds, causing client timeouts
4. **Poor User Experience**: Users waiting for long periods without feedback
5. **Resource Blocking**: Synchronous operations blocking other requests

### Current Architecture Pain Points
- Single-threaded blocking operations
- No progress indication for users
- HTTP timeout limitations (typically 30-60 seconds)
- Resource intensive geo-spatial calculations
- Multiple sequential database queries for availability checks

## Decision
Implement an **asynchronous job queue system** for facility searches with the following architecture:

### 1. Two-Endpoint Pattern
- **`POST /search/start`**: Immediately returns a jobId, queues search in background
- **`GET /search/result/:jobId`**: Returns current status and results when available

### 2. Job States Management
```
pending → processing → completed/failed/cancelled
```

### 3. Database Storage Approach
Use MySQL database for job persistence instead of in-memory solutions for:
- Durability across server restarts
- Audit trail capabilities
- Simple deployment (no additional infrastructure)

### 4. Background Processing
- Use `setImmediate()` for background job execution
- Extract search logic into separate reusable module
- Maintain original search functionality intact