# Game Note Backend

A Go REST API backend for the Game Note Flutter application.

## 🚨 IMMEDIATE ACTION PLAN - PHASE 1 PRIORITIES

### 🔥 Critical Path (DO FIRST - NO EXCEPTIONS)

1. **Data Backup Strategy** - Complete before ANY code changes
   - Export ALL Firestore collections to secure storage
   - Verify backup integrity and restoration procedures
   - Set up automated daily backups during migration

2. **Feature Flags System** - Enable safe rollout and rollback
   - Remote configuration for instant feature toggling
   - Emergency kill-switch for immediate rollback
   - A/B testing infrastructure for each migration phase

3. **Monitoring & Alerting** - Detect issues immediately
   - Real-time performance metrics and error tracking
   - Automatic alerts for critical thresholds
   - Migration health dashboard with success metrics

4. **Rollback Procedures** - Prepare for worst-case scenarios
   - Phase-specific rollback scripts and documentation
   - Rollback testing in staging environment
   - Emergency communication plan

### ⚡ Next Development Steps (After Risk Mitigation)

1. **PostgreSQL Setup** - Foundation database infrastructure

2. **Firebase Auth Middleware** - Secure token validation

3. **Database Schema** - Optimized for performance

4. **API Structure** - Clean architecture setup

## Quick Start

### Prerequisites

- Go 1.19 or higher
- Git

### Installation

    1. Clone and navigate to the backend directory:

    ```bash
    cd game_note_backend
    ```

    2. Install dependencies:

    ```bash
    go mod tidy
    ```

    3. Run the server:

    ```bash
    go run main.go
    ```

    The server will start on port 8080 by default.

### API Endpoints

- `GET /health` - Health check endpoint
- `GET /hello` - Test endpoint returning a hello message

### Environment Variables

- `PORT` - Server port (default: 8080)

### Testing

Test the endpoints:

    ```bash
    # Health check
    curl http://localhost:8080/health

    # Hello endpoint
    curl http://localhost:8080/hello
    ```

## Development

### Project Structure

    ```bash
    game_note_backend/
    ├── main.go          # Main server file
    ├── go.mod           # Go module file
    ├── go.sum           # Go dependencies checksum
    └── README.md        # This file
    ```

## Migration Strategy

This backend will replace Firestore as the database layer while keeping Firebase Auth for authentication. The migration is broken down into phases for manageable implementation.

### Phase 1: Critical Risk Mitigation (HIGH PRIORITY - MUST COMPLETE FIRST)

- [ ] **1.1** 🚨 Create comprehensive data backup strategy (BEFORE ANY MIGRATION)
  - [ ] Complete Firestore export scripts for ALL collections (users, tournaments, teams, matches, chat)
  - [ ] Automated backup verification and integrity checks
  - [ ] Multiple backup storage locations and retention policy
  - [ ] Test data restoration procedures
  - [ ] Schedule automated daily backups during migration
- [ ] **1.2** 🚨 Build feature flags system for gradual rollout
  - [ ] Feature toggle infrastructure with remote configuration
  - [ ] Per-user and per-feature rollout controls
  - [ ] A/B testing capability for each migration phase
  - [ ] Emergency kill-switch for instant rollback
  - [ ] Integration with Flutter app for seamless switching
- [ ] **1.3** 🚨 Set up comprehensive monitoring and alerting
  - [ ] Real-time application metrics (response times, error rates, memory usage)
  - [ ] Database performance monitoring with query analysis
  - [ ] Real-time alerting system (email, Slack, SMS for critical issues)
  - [ ] Performance baseline establishment from current Firestore metrics
  - [ ] Migration health dashboard with key success metrics
- [ ] **1.4** 🚨 Create detailed rollback procedures for each phase
  - [ ] Phase-specific rollback scripts and procedures
  - [ ] Emergency rollback documentation with step-by-step instructions
  - [ ] Rollback testing in staging environment for all phases
  - [ ] Data synchronization procedures during rollback
  - [ ] Communication plan for rollback scenarios

### Phase 1.5: Foundation Setup (MEDIUM PRIORITY)

- [ ] **1.5** Add PostgreSQL database with optimized configuration
  - [ ] Connection pooling for concurrent users (min 10, max 100 connections)
  - [ ] Database performance optimization (shared_buffers, work_mem, etc.)
  - [ ] Read replicas setup for read-heavy operations
- [ ] **1.6** Implement secure Firebase Auth token validation
  - [ ] Firebase JWT validation middleware with proper error handling
  - [ ] Security audit of token validation (SQL injection, XSS prevention)
  - [ ] Rate limiting and DDoS protection (100 requests/minute per user)
  - [ ] Request validation and sanitization
- [ ] **1.7** Create performance-optimized database schema
  - [ ] Schema design optimized for read-heavy operations
  - [ ] Proper indexing strategy (B-tree for equality, GIN for arrays/JSON)
  - [ ] Foreign key constraints for data integrity
  - [ ] Database migration scripts with rollback capability
- [ ] **1.8** Set up clean project structure
  - [ ] Models, repositories, handlers, middleware packages
  - [ ] Dependency injection setup
  - [ ] Error handling and logging framework
- [ ] **1.9** Add environment configuration and structured logging
  - [ ] Environment-specific configurations (dev, staging, prod)
  - [ ] Structured JSON logging with request tracing
  - [ ] Log aggregation setup (ELK stack or similar)

### Phase 2: Core API Development

- [ ] **2.1** User management API endpoints
  - [ ] `GET /api/users/:id/profile` - Get user profile
  - [ ] `PUT /api/users/:id/profile` - Update user profile
  - [ ] `POST /api/users` - Create user record (on first Firebase login)
- [ ] **2.2** Team management API endpoints
  - [ ] `GET /api/teams` - List teams
  - [ ] `POST /api/teams` - Create team
  - [ ] `GET /api/teams/:id` - Get team details
  - [ ] `PUT /api/teams/:id` - Update team
  - [ ] `DELETE /api/teams/:id` - Delete team
- [ ] **2.3** Tournament/League management API endpoints
  - [ ] `GET /api/tournaments` - List tournaments
  - [ ] `POST /api/tournaments` - Create tournament
  - [ ] `GET /api/tournaments/:id` - Get tournament details
  - [ ] `PUT /api/tournaments/:id` - Update tournament
  - [ ] `DELETE /api/tournaments/:id` - Delete tournament

### Phase 3: Advanced Features

- [ ] **3.1** Match management API endpoints
  - [ ] `GET /api/tournaments/:id/matches` - List matches
  - [ ] `POST /api/tournaments/:id/matches` - Create match
  - [ ] `PUT /api/matches/:id` - Update match score/status
  - [ ] `DELETE /api/matches/:id` - Delete match
- [ ] **3.2** Group/Community API endpoints
  - [ ] `GET /api/groups` - List groups
  - [ ] `POST /api/groups` - Create group
  - [ ] `GET /api/groups/:id/members` - Get group members
  - [ ] `POST /api/groups/:id/members` - Add member to group
  - [ ] `DELETE /api/groups/:id/members/:userId` - Remove member
- [ ] **3.3** Chat system API endpoints
  - [ ] `GET /api/chat/:groupId/messages` - Get chat messages
  - [ ] `POST /api/chat/:groupId/messages` - Send message
  - [ ] `PUT /api/chat/messages/:id` - Edit message
  - [ ] `DELETE /api/chat/messages/:id` - Delete message

### Phase 4: Real-time Features

- [ ] **4.1** WebSocket connection management
- [ ] **4.2** Real-time tournament updates
- [ ] **4.3** Live chat messaging
- [ ] **4.4** Match score live updates
- [ ] **4.5** Notification broadcasting

### Phase 5: Data Migration

- [ ] **5.1** Export data from Firestore collections
- [ ] **5.2** Transform and import data to PostgreSQL
- [ ] **5.3** Verify data integrity and relationships
- [ ] **5.4** Create data backup and rollback procedures

### Phase 6: Flutter App Integration

- [ ] **6.1** Create HTTP client service in Flutter app
- [ ] **6.2** Update repository implementations to use REST API
- [ ] **6.3** Replace Firestore streams with WebSocket connections
- [ ] **6.4** Update dependency injection configuration
- [ ] **6.5** Add feature flags for gradual rollout

### Phase 7: Testing, Performance & Security

- [ ] **7.1** Performance testing with realistic data volumes
  - [ ] Load testing with concurrent users
  - [ ] Database query performance optimization
  - [ ] Memory usage monitoring under load
  - [ ] API response time benchmarking (target: <200ms for reads)
- [ ] **7.2** Comprehensive API testing
  - [ ] Unit tests for all endpoints
  - [ ] Integration tests for complete workflows
  - [ ] Error handling and edge case testing
- [ ] **7.3** Security audit and penetration testing
  - [ ] Firebase token validation security review
  - [ ] SQL injection prevention verification
  - [ ] Rate limiting effectiveness testing
  - [ ] Authentication bypass attempt testing
- [ ] **7.4** Production deployment setup
  - [ ] Container orchestration and scaling
  - [ ] Database backup and recovery procedures
  - [ ] SSL/TLS configuration and security
- [ ] **7.5** Advanced monitoring and logging setup
  - [ ] Performance metrics dashboard
  - [ ] Error tracking and alerting
  - [ ] Real-time system health monitoring

### Phase 8: Rollout & Cleanup

- [ ] **8.1** Gradual feature rollout with feature flags
- [ ] **8.2** Monitor performance and error rates
- [ ] **8.3** Complete migration and remove Firestore dependencies
- [ ] **8.4** Clean up old Firestore collections
- [ ] **8.5** Update documentation and deployment guides

## 🎯 SUCCESS METRICS & PERFORMANCE TARGETS

### 📊 Performance Requirements (MUST ACHIEVE)

- **API Response Times**: < 200ms for 95% of requests (current Firestore baseline: measure first)
- **Real-time Updates**: < 1 second latency for live features (tournaments, chat)
- **Error Rate**: < 0.1% across all endpoints (99.9% uptime)
- **Database Query Performance**: < 50ms for 90% of queries
- **Concurrent User Support**: 1000+ simultaneous users without degradation
- **Data Consistency**: 100% data integrity during migration (zero data loss)

### 🚨 Critical Thresholds (Alert Triggers)

- API response time > 500ms (immediate alert)
- Error rate > 1% (escalation alert)
- Database connection pool exhaustion (> 90% utilization)
- Memory usage > 80% (scaling alert)
- Disk space > 85% (capacity alert)
- Real-time message delay > 5 seconds (user experience alert)
- Failed authentication rate > 5% (security alert)

### 📈 Migration Health Indicators

- **Phase Completion Rate**: Each phase must achieve 95% success before proceeding
- **User Satisfaction**: No degradation in app store ratings during migration
- **Feature Parity**: 100% feature compatibility before removing Firestore
- **Rollback Frequency**: < 1 rollback per phase (max 2 rollbacks total)

### 📋 Monitoring Dashboard

- [ ] API endpoint response time tracking with 95th percentile metrics
- [ ] Database connection pool utilization and wait times
- [ ] WebSocket connection count, stability, and message latency
- [ ] Memory usage patterns and garbage collection frequency
- [ ] Error rate by endpoint with detailed error categorization
- [ ] User experience metrics (app crashes, timeouts, loading times)
- [ ] Real-time feature performance (chat delivery, live updates)

### ✅ Migration Health Checks

- [ ] Data consistency validation between Firestore and PostgreSQL
- [ ] Feature flag rollout success rates and user adoption
- [ ] Rollback procedure effectiveness testing (quarterly drills)
- [ ] Real-time feature parity verification with automated tests
- [ ] Security audit compliance verification and penetration testing

## Implementation Notes

### Architecture Decisions

- **Hybrid Approach**: Keep Firebase Auth, replace Firestore with PostgreSQL
- **Clean Architecture**: Repository pattern, dependency injection
- **Real-time**: WebSockets for live features (replacing Firestore listeners)
- **Security**: Firebase JWT validation on all API endpoints

### Database Design Principles

- Use Firebase UID as primary key for user-related tables
- Maintain referential integrity with foreign keys
- Optimize for read-heavy operations (tournaments, matches, chat)
- Index frequently queried fields

### API Design Standards

- RESTful endpoints with consistent naming
- JSON request/response format
- Proper HTTP status codes
- Error handling with structured error responses
- Pagination for list endpoints
- Rate limiting and request validation

### Current Status

✅ **Basic server setup completed** - Hello endpoint working  
🚧 **Ready for Phase 1** - Foundation setup

## Development Guidelines

For detailed Copilot instructions and development guidelines, see [`.copilot-instructions.md`](.copilot-instructions.md).

This includes:

- Project context and architecture decisions
- Flutter app structure references
- Go backend development patterns
- Data migration notes
- Session continuity guidelines
