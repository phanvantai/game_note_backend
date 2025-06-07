# Copilot Instructions: Game Note Migration Project

## 🚨 CRITICAL MIGRATION PRIORITIES - READ FIRST

### Phase 1 MUST BE COMPLETED FIRST (Risk Mitigation)

**⚠️ DO NOT PROCEED TO CODE DEVELOPMENT WITHOUT COMPLETING THESE:**

1. **Data Backup Strategy** - BEFORE any migration work:
   - Complete Firestore export for ALL collections
   - Automated backup verification and integrity checks
   - Multiple backup locations and retention policy
   - Test restoration procedures thoroughly

2. **Feature Flags System** - Enable safe rollout:
   - Remote configuration infrastructure
   - Per-user and per-feature rollout controls
   - Emergency kill-switch for instant rollback
   - A/B testing capability for migration phases

3. **Monitoring & Alerting** - Detect issues immediately:
   - Real-time performance metrics (API response, memory, errors)
   - Database performance monitoring with query analysis
   - Automatic alerting system (email, Slack, SMS for critical issues)
   - Migration health dashboard with success metrics

4. **Rollback Procedures** - Prepare for worst-case scenarios:
   - Phase-specific rollback scripts and procedures
   - Emergency rollback documentation with step-by-step instructions
   - Rollback testing in staging environment for all phases
   - Communication plan for rollback scenarios

### 🎯 Success Metrics & Performance Targets

- **API Response Times**: < 200ms for 95% of requests
- **Real-time Updates**: < 1 second latency
- **Error Rate**: < 0.1% (99.9% uptime)
- **Database Queries**: < 50ms for 90% of queries
- **Concurrent Users**: 1000+ without degradation
- **Data Integrity**: 100% (zero data loss)

## Project Context

- **Migration Goal**: Replace Firestore database with PostgreSQL backend while keeping Firebase Auth
- **Flutter App Location**: `../game_note/` (sibling directory)
- **Backend Location**: `./` (current `game_note_backend/` directory)
- **Current Phase**: Check README.md for current status and next steps

## Key Architecture Decisions to Remember

1. **Hybrid Approach**: Firebase Auth stays, only Firestore is being replaced
2. **Clean Architecture**: Repository pattern in both Flutter app and Go backend
3. **Real-time**: Replace Firestore streams with WebSockets
4. **Authentication**: Firebase JWT tokens validated by Go backend middleware

## Flutter App Structure (Important Files)

- `lib/injection_container.dart` - Dependency injection (120+ lines, needs updates for new repos)
- `lib/data/repositories/` - Repository implementations to be replaced
- `lib/firebase/firestore/` - Firestore services to be replaced with HTTP clients
- `lib/firebase/auth/gn_auth.dart` - Keep unchanged (Firebase Auth)
- `lib/firebase/messaging/gn_firebase_messaging.dart` - Keep unchanged (FCM)

## Go Backend Guidelines

- Use Gorilla Mux for routing
- Implement repository pattern matching Flutter app structure
- Firebase Admin SDK for JWT validation
- PostgreSQL with proper indexing for read-heavy operations
- WebSocket manager for real-time features

## Development Workflow

1. Always check current phase status in README.md
2. Reference existing Flutter repository interfaces when creating Go equivalents
3. Maintain same data models/structures between Flutter and Go
4. Test each endpoint before moving to next phase
5. Update README.md checkboxes as tasks are completed

## Common Commands

```bash
# Go backend development
cd game_note_backend
go run main.go
go get [package]
go mod tidy

# Flutter app reference
cd ../game_note
flutter pub get
flutter analyze
```

## Data Migration Notes

- Firebase UID is primary key for user-related tables
- Preserve existing data relationships
- Export from Firestore collections: users, tournaments, teams, matches, groups, chat_messages
- PostgreSQL tables should match Firestore document structure initially

## Session Continuity

- Always check Phase status before starting work
- Review previous implementation patterns in existing Flutter repositories
- Maintain consistent error handling and response formats
- Update documentation as features are implemented

## Repository Pattern Examples (Flutter)

Reference these existing Flutter repositories when creating Go equivalents:

- `UserRepository` → User management API
- `TeamRepository` → Team management API
- `EsportLeagueRepository` → Tournament management API
- `EsportGroupRepository` → Group management API
- `EsportChatRepository` → Chat system API
- `NotificationRepository` → Notification API

## Error Handling Standards

- Use structured error responses in JSON format
- Implement proper HTTP status codes (200, 201, 400, 401, 403, 404, 500)
- Log errors with context for debugging
- Return user-friendly error messages

## Security Guidelines

- Validate Firebase JWT tokens on all protected endpoints
- Extract user UID from validated tokens
- Implement rate limiting on public endpoints
- Sanitize all user inputs
- Use prepared statements for SQL queries
