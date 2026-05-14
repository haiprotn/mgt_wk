# 📁 Project Folder Structure & Organization

**Document Version:** 1.0  
**Last Updated:** 2026-05-14  
**Status:** Production Ready ✓

---

## Directory Tree Overview

```
mgt_wk/
├── 📄 README.md                          # Project overview
├── 📄 .gitignore                         # Git ignore rules
├── 📄 .github/                           # GitHub workflows
├── 📄 docker-compose.yml                 # Local development setup
│
├── 📁 docs/                              # 📚 DOCUMENTATION
│   ├── ARCHITECTURE.md
│   ├── FOLDER_STRUCTURE.md               (this file)
│   ├── DATABASE_DESIGN.md
│   ├── SERVICE_ARCHITECTURE.md
│   ├── API_STRATEGY.md
│   ├── SECURITY_STRATEGY.md
│   ├── SCALABILITY_STRATEGY.md
│   ├── DEPLOYMENT_GUIDE.md
│   └── TROUBLESHOOTING.md
│
├── 📁 backend/                           # 🔧 DJANGO MICROSERVICES
│   │
│   ├── 📁 shared/                        # Shared utilities across services
│   │   ├── __init__.py
│   │   ├── 📁 auth/                      # Authentication helpers
│   │   │   ├── __init__.py
│   │   │   ├── jwt_utils.py              # JWT token generation/validation
│   │   │   ├── oauth.py                  # OAuth2 providers
│   │   │   ├── permissions.py            # RBAC permissions
│   │   │   └── decorators.py             # Auth decorators
│   │   │
│   │   ├── 📁 models/                    # Base models
│   │   │   ├── __init__.py
│   │   │   ├── base_model.py             # Abstract base model
│   │   │   ├── tenant_model.py           # Multi-tenant model
│   │   │   └── audit_model.py            # Audit trail model
│   │   │
│   │   ├── 📁 utils/                     # Utility functions
│   │   │   ├── __init__.py
│   │   │   ├── decorators.py             # Custom decorators
│   │   │   ├── validators.py             # Field validators
│   │   │   ├── formatters.py             # Data formatters
│   │   │   ├── exceptions.py             # Custom exceptions
│   │   │   └── constants.py              # App constants
│   │   │
│   │   ├── 📁 cache/                     # Caching utilities
│   │   │   ├── __init__.py
│   │   │   ├── redis_client.py           # Redis connection
│   │   │   ├── decorators.py             # Cache decorators
│   │   │   └── keys.py                   # Cache key generation
│   │   │
│   │   ├── 📁 celery/                    # Celery configuration
│   │   │   ├── __init__.py
│   │   │   ├── config.py                 # Celery config
│   │   │   ├── tasks.py                  # Base tasks
│   │   │   └── celery.py                 # Celery app
│   │   │
│   │   ├── 📁 logging/                   # Logging configuration
│   │   │   ├── __init__.py
│   │   │   ├── config.py                 # Logging setup
│   │   │   └── formatters.py             # Custom formatters
│   │   │
│   │   ├── 📁 middleware/                # Django middleware
│   │   │   ├── __init__.py
│   │   │   ├── auth_middleware.py        # Auth validation
│   │   │   ├── tenant_middleware.py      # Tenant isolation
│   │   │   ├── error_middleware.py       # Error handling
│   │   │   └── logging_middleware.py     # Request logging
│   │   │
│   │   ├── 📁 serializers/               # Shared serializers
│   │   │   ├── __init__.py
│   │   │   ├── base_serializer.py
│   │   │   └── common_serializers.py
│   │   │
│   │   ├── 📁 tests/                     # Shared test utilities
│   │   │   ├── __init__.py
│   │   │   ├── base_testcase.py
│   │   │   ├── factories.py              # Test data factories
│   │   │   └── fixtures.py
│   │   │
│   │   └── 📁 migrations/                # Database migrations
│   │       └── (shared migrations)
│   │
│   ├── 📁 services/                      # Individual microservices
│   │   │
│   │   ├── 📁 auth-service/              # 🔐 Authentication Service
│   │   │   ├── manage.py
│   │   │   ├── requirements.txt
│   │   │   ├── Dockerfile
│   │   │   │
│   │   │   ├── 📁 config/                # Service configuration
│   │   │   │   ├── __init__.py
│   │   │   │   ├── settings.py           # Django settings
│   │   │   │   ├── urls.py               # URL routing
│   │   │   │   ├── wsgi.py               # WSGI application
│   │   │   │   └── asgi.py               # ASGI application
│   │   │   │
│   │   │   ├── 📁 apps/                  # Django apps
│   │   │   │   ├── users/
│   │   │   │   │   ├── __init__.py
│   │   │   │   │   ├── models.py         # User model
│   │   │   │   │   ├── views.py          # User endpoints
│   │   │   │   │   ├── serializers.py    # Serializers
│   │   │   │   │   ├── filters.py        # Filters
│   │   │   │   │   ├── permissions.py    # Permissions
│   │   │   │   │   ├── urls.py           # Routes
│   │   │   │   │   └── tests/
│   │   │   │   │
│   │   │   │   ├── auth/
│   │   │   │   │   ├── __init__.py
│   │   │   │   │   ├── models.py         # Token model
│   │   │   │   │   ├── views.py          # Login/logout
│   │   │   │   │   ├── serializers.py    # Auth serializers
│   │   │   │   │   ├── backends.py       # Auth backends
│   │   │   │   │   ├── urls.py
│   │   │   │   │   └── tests/
│   │   │   │   │
│   │   │   │   ├── oauth/
│   │   │   │   │   ├── __init__.py
│   │   │   │   │   ├── providers.py      # OAuth providers
│   │   │   │   │   ├── views.py          # OAuth endpoints
│   │   │   │   │   ├── serializers.py
│   │   │   │   │   └── tests/
│   │   │   │   │
│   │   │   │   └── mfa/
│   │   │   │       ├── __init__.py
│   │   │   │       ├── models.py         # MFA model
│   │   │   │       ├── views.py          # MFA endpoints
│   │   │   │       ├── services.py       # MFA logic
│   │   │   │       └── tests/
│   │   │   │
│   │   │   ├── 📁 migrations/
│   │   │   │   └── (service-specific migrations)
│   │   │   │
│   │   │   └── 📁 tests/
│   │   │       └── (integration tests)
│   │   │
│   │   ├── 📁 task-service/              # ✅ Task Service
│   │   │   └── (similar structure as auth-service)
│   │   │
│   │   ├── 📁 material-service/          # 📦 Material Service
│   │   │   └── (similar structure as auth-service)
│   │   │
│   │   ├── 📁 hr-service/                # 👥 HR Service
│   │   │   └── (similar structure as auth-service)
│   │   │
│   │   ├── 📁 gps-service/               # 📍 GPS Service
│   │   │   └── (similar structure as auth-service)
│   │   │
│   │   └── 📁 dashboard-service/         # 📈 Dashboard Service
│   │       └── (similar structure as auth-service)
│   │
│   ├── 📁 config/                        # Global configuration
│   │   ├── __init__.py
│   │   ├── docker-compose.yml
│   │   ├── nginx.conf                    # Nginx config
│   │   └── supervisor.conf               # Supervisor config
│   │
│   └── 📁 scripts/                       # Utility scripts
│       ├── setup_db.py                   # Database setup
│       ├── seed_data.py                  # Seed test data
│       └── cleanup.py                    # Cleanup script
│
├── 📁 frontend/                          # 🌐 Next.js Dashboard
│   ├── package.json
│   ├── package-lock.json
│   ├── tsconfig.json
│   ├── tailwind.config.js
│   ├── next.config.js
│   │
│   ├── 📁 public/                        # Static assets
│   │   ├── favicon.ico
│   │   ├── logo.svg
│   │   └── icons/
│   │
│   ├── 📁 app/                           # App router (Next.js 13+)
│   │   ├── layout.tsx                    # Root layout
│   │   ├── page.tsx                      # Home page
│   │   │
│   │   ├── 📁 (auth)/                    # Auth pages group
│   │   │   ├── login/page.tsx
│   │   │   ├── signup/page.tsx
│   │   │   ├── forgot-password/page.tsx
│   │   │   └── layout.tsx
│   │   │
│   │   ├── 📁 dashboard/                 # Dashboard layout
│   │   │   ├── layout.tsx
│   │   │   │
│   │   │   ├── 📁 (overview)/
│   │   │   │   ├── page.tsx              # Dashboard overview
│   │   │   │   ├── layout.tsx
│   │   │   │   └── components/
│   │   │   │
│   │   │   ├── 📁 tasks/                 # Tasks section
│   │   │   │   ├── page.tsx
│   │   │   │   ├── [id]/
│   │   │   │   │   ├── page.tsx          # Task detail
│   │   │   │   │   └── edit/page.tsx
│   │   │   │   ├── layout.tsx
│   │   │   │   └── components/
│   │   │   │
│   │   │   ├── 📁 materials/             # Materials section
│   │   │   │   ├── page.tsx
│   │   │   │   ├── [id]/page.tsx
│   │   │   │   └── layout.tsx
│   │   │   │
│   │   │   ├── 📁 employees/             # Employees section
│   │   │   │   ├── page.tsx
│   │   │   │   ├── [id]/page.tsx
│   │   │   │   └── layout.tsx
│   │   │   │
│   │   │   ├── 📁 gps/                   # GPS/Tracking section
│   │   │   │   ├── page.tsx
│   │   │   │   └── layout.tsx
│   │   │   │
│   │   │   ├── 📁 reports/               # Reports section
│   │   │   │   ├── page.tsx
│   │   │   │   ├── [reportId]/page.tsx
│   │   │   │   └── layout.tsx
│   │   │   │
│   │   │   ├── 📁 settings/              # Settings section
│   │   │   │   ├── page.tsx
│   │   │   │   ├── profile/page.tsx
│   │   │   │   ├── organization/page.tsx
│   │   │   │   ├── security/page.tsx
│   │   │   │   └── layout.tsx
│   │   │   │
│   │   │   └── 📁 admin/                 # Admin section
│   │   │       ├── page.tsx
│   │   │       ├── users/page.tsx
│   │   │       ├── tenants/page.tsx
│   │   │       └── layout.tsx
│   │   │
│   │   ├── 📁 api/                       # API routes (proxy)
│   │   │   ├── auth/[...slug]/route.ts
│   │   │   ├── tasks/[...slug]/route.ts
│   │   │   └── [...slug]/route.ts
│   │   │
│   │   └── 📁 error/
│   │       ├── 404.tsx
│   │       ├── 500.tsx
│   │       └── error.tsx
│   │
│   ├── 📁 components/                    # Reusable components
│   │   ├── 📁 common/                    # Generic components
│   │   │   ├── Header.tsx
│   │   │   ├── Sidebar.tsx
│   │   │   ├── Card.tsx
│   │   │   ├── Modal.tsx
│   │   │   ├── Button.tsx
│   │   │   ├── Form.tsx
│   │   │   ├── Table.tsx
│   │   │   ├── Pagination.tsx
│   │   │   ├── Loading.tsx
│   │   │   ├── Error.tsx
│   │   │   └── Toast.tsx
│   │   │
│   │   ├── 📁 dashboard/                 # Dashboard-specific
│   │   │   ├── StatCard.tsx
│   │   │   ├── Chart.tsx
│   │   │   ├── KpiWidget.tsx
│   │   │   └── MetricsPanel.tsx
│   │   │
│   │   ├── 📁 forms/                     # Form components
│   │   │   ├── TaskForm.tsx
│   │   │   ├── MaterialForm.tsx
│   │   │   ├── EmployeeForm.tsx
│   │   │   └── FilterForm.tsx
│   │   │
│   │   ├── 📁 layout/                    # Layout components
│   │   │   ├── Navigation.tsx
│   │   │   ├── Breadcrumb.tsx
│   │   │   └── Footer.tsx
│   │   │
│   │   └── 📁 charts/                    # Chart components
│   │       ├── BarChart.tsx
│   │       ├── LineChart.tsx
│   │       ├── PieChart.tsx
│   │       └── GaugeChart.tsx
│   │
│   ├── 📁 lib/                           # Utility functions
│   │   ├── 📁 api/
│   │   │   ├── client.ts                 # API client
│   │   │   ├── endpoints.ts              # API endpoints
│   │   │   └── interceptors.ts           # Request/response interceptors
│   │   │
│   │   ├── 📁 hooks/                     # Custom React hooks
│   │   │   ├── useAuth.ts
│   │   │   ├── useQuery.ts
│   │   │   ├── useFetch.ts
│   │   │   ├── useLocalStorage.ts
│   │   │   ├── useDebounce.ts
│   │   │   └── useTheme.ts
│   │   │
│   │   ├── 📁 store/                     # Redux/Zustand state
│   │   │   ├── authStore.ts
│   │   │   ├── dashboardStore.ts
│   │   │   └── uiStore.ts
│   │   │
│   │   ├── 📁 utils/
│   │   │   ├── date.ts                   # Date utilities
│   │   │   ├── format.ts                 # Formatting utilities
│   │   │   ├── validators.ts             # Validation functions
│   │   │   ├── constants.ts              # App constants
│   │   │   └── helpers.ts
│   │   │
│   │   ├── 📁 services/
│   │   │   ├── authService.ts
│   │   │   ├── taskService.ts
│   │   │   ├── materialService.ts
│   │   │   ├── hrService.ts
│   │   │   └── gpsService.ts
│   │   │
│   │   └── 📁 types/
│   │       ├── index.ts
│   │       ├── api.ts
│   │       ├── domain.ts
│   │       └── common.ts
│   │
│   ├── 📁 styles/                        # Global styles
│   │   ├── globals.css
│   │   ├── variables.css
│   │   └── animations.css
│   │
│   └── 📁 __tests__/
│       ├── 📁 unit/
│       ├── 📁 integration/
│       └── 📁 e2e/
│
├── 📁 mobile/                            # 📱 Flutter App
│   ├── pubspec.yaml                      # Flutter dependencies
│   ├── pubspec.lock
│   ├── analysis_options.yaml
│   ├── .gitignore
│   │
│   ├── 📁 lib/                           # Main code
│   │   ├── main.dart                     # Entry point
│   │   │
│   │   ├── 📁 models/                    # Data models
│   │   │   ├── user_model.dart
│   │   │   ├── task_model.dart
│   │   │   ├── material_model.dart
│   │   │   ├── employee_model.dart
│   │   │   ├── location_model.dart
│   │   │   └── response_model.dart
│   │   │
│   │   ├── 📁 screens/                   # Pages/Screens
│   │   │   ├── 📁 auth/
│   │   │   │   ├── login_screen.dart
│   │   │   │   ├── signup_screen.dart
│   │   │   │   ├── forgot_password_screen.dart
│   │   │   │   └── mfa_screen.dart
│   │   │   │
│   │   │   ├── 📁 home/
│   │   │   │   ├── home_screen.dart
│   │   │   │   ├��─ dashboard_screen.dart
│   │   │   │   └── home_widgets.dart
│   │   │   │
│   │   │   ├── 📁 tasks/
│   │   │   │   ├── tasks_screen.dart
│   │   │   │   ├── task_detail_screen.dart
│   │   │   │   ├── create_task_screen.dart
│   │   │   │   └── task_widgets.dart
│   │   │   │
│   │   │   ├── 📁 materials/
│   │   │   │   ├── materials_screen.dart
│   │   │   │   ├── material_detail_screen.dart
│   │   │   │   └── material_widgets.dart
│   │   │   │
│   │   │   ├── 📁 gps/
│   │   │   │   ├── gps_screen.dart        # Map view
│   │   │   │   ├── tracking_screen.dart
│   │   │   │   ├── attendance_screen.dart
│   │   │   │   └── gps_widgets.dart
│   │   │   │
│   │   │   ├── 📁 profile/
│   │   │   │   ├── profile_screen.dart
│   │   │   │   ├── settings_screen.dart
│   │   │   │   └── edit_profile_screen.dart
│   │   │   │
│   │   │   └── 📁 common/
│   │   │       ├── splash_screen.dart
│   │   │       ├── loading_screen.dart
│   │   │       └── error_screen.dart
│   │   │
│   │   ├── 📁 widgets/                   # Reusable widgets
│   │   │   ├── custom_app_bar.dart
│   │   │   ├── custom_drawer.dart
│   │   │   ├── custom_button.dart
│   │   │   ├── custom_text_field.dart
│   │   │   ├── custom_card.dart
│   │   │   ├── loading_widget.dart
│   │   │   ├── error_widget.dart
│   │   │   ├── empty_state_widget.dart
│   │   │   └── custom_dialog.dart
│   │   │
│   │   ├── 📁 services/                  # Service layer
│   │   │   ├── api_service.dart          # HTTP client
│   │   │   ├── auth_service.dart
│   │   │   ├── task_service.dart
│   │   │   ├── material_service.dart
│   │   │   ├── gps_service.dart          # Location tracking
│   │   │   ├── notification_service.dart # Push notifications
│   │   │   ├── storage_service.dart      # Local storage
│   │   │   └── sync_service.dart         # Offline sync
│   │   │
│   │   ├── 📁 providers/                 # State management
│   │   │   ├── auth_provider.dart        # (using GetX/Riverpod)
│   │   │   ├── task_provider.dart
│   │   │   ├── material_provider.dart
│   │   │   ├── gps_provider.dart
│   │   │   ├── ui_provider.dart
│   │   │   └── sync_provider.dart
│   │   │
│   │   ├── 📁 utils/
│   │   │   ├── constants.dart             # App constants
│   │   │   ├── date_utils.dart           # Date formatting
│   │   │   ├── validators.dart           # Form validators
│   │   │   ├── logger.dart               # Logging
│   │   │   ├── permissions_handler.dart  # Permissions
│   │   │   └── helpers.dart
│   │   │
│   │   ├── 📁 theme/
│   │   │   ├── app_theme.dart
│   │   │   ├── app_colors.dart
│   │   │   ├── app_typography.dart
│   │   │   └── app_dimensions.dart
│   │   │
│   │   ├── 📁 network/
│   │   │   ├── api_client.dart           # Dio/HTTP client
│   │   │   ├── interceptors.dart         # Request/response
│   │   │   ├── network_exceptions.dart
│   │   │   └── connection_checker.dart
│   │   │
│   │   ├── 📁 local_db/
│   │   │   ├── app_database.dart         # SQLite DB
│   │   │   ├── 📁 daos/
│   │   │   │   ├── task_dao.dart
│   │   │   │   ├── material_dao.dart
│   │   │   │   └── employee_dao.dart
│   │   │   └── 📁 entities/
│   │   │       ├── task_entity.dart
│   │   │       ├── material_entity.dart
│   │   │       └── employee_entity.dart
│   │   │
│   │   └── 📁 config/
│   │       ├── app_config.dart
│   │       └── dependency_injection.dart  # GetIt setup
│   │
│   ├── 📁 test/
│   │   ├── 📁 unit/
│   │   ├── 📁 widget/
│   │   └── 📁 integration/
│   │
│   └── 📁 android/
│       ├── app/build.gradle
│       └── AndroidManifest.xml
│
│   └── 📁 ios/
│       ├── Podfile
│       └── Info.plist
│
├── 📁 infrastructure/                    # 🚀 DEVOPS & INFRA
│   │
│   ├── 📁 kubernetes/                    # K8s manifests
│   │   ├── 📁 namespaces/
│   │   │   └── dev.yaml, staging.yaml, prod.yaml
│   │   │
│   │   ├── 📁 services/
│   │   │   ├── auth-service.yaml
│   │   │   ├── task-service.yaml
│   │   │   ├── material-service.yaml
│   │   │   ├── hr-service.yaml
│   │   │   ├── gps-service.yaml
│   │   │   └── dashboard-service.yaml
│   │   │
│   │   ├── 📁 deployments/
│   │   │   ├── auth-deployment.yaml
│   │   │   ├── task-deployment.yaml
│   │   │   └── (other deployments)
│   │   │
│   │   ├── 📁 statefulsets/
│   │   │   ├── postgres-statefulset.yaml
│   │   │   ├── redis-statefulset.yaml
│   │   │   └── rabbitmq-statefulset.yaml
│   │   │
│   │   ├── 📁 configmaps/
│   │   │   ├── app-config.yaml
│   │   │   ├── logging-config.yaml
│   │   │   └── nginx-config.yaml
│   │   │
│   │   ├── 📁 secrets/
│   │   │   ├── db-credentials.yaml
│   │   │   ├── api-keys.yaml
│   │   │   └── tls-certificates.yaml
│   │   │
│   │   ├── 📁 ingress/
│   │   │   └── ingress.yaml
│   │   │
│   │   ├── 📁 hpa/
│   │   │   └── autoscaling.yaml
│   │   │
│   │   ├── 📁 pvc/
│   │   │   ├── postgres-pvc.yaml
│   │   │   └── redis-pvc.yaml
│   │   │
│   │   └── kustomization.yaml
│   │
│   ├── 📁 terraform/                     # Infrastructure as Code
│   │   ├── main.tf                       # Main config
│   │   ├── variables.tf                  # Variables
│   │   ├── outputs.tf                    # Outputs
│   │   ├── vpc.tf                        # VPC setup
│   │   ├── eks.tf                        # EKS cluster
│   │   ├── rds.tf                        # RDS (PostgreSQL)
│   │   ├── elasticache.tf                # Redis
│   │   ├── s3.tf                         # S3 buckets
│   │   ├── iam.tf                        # IAM roles
│   │   ├── security_groups.tf            # Security groups
│   │   ├── load_balancer.tf              # ALB/NLB
│   │   ├── 📁 modules/                   # Reusable modules
│   │   │   ├── eks/
│   │   │   ├── rds/
│   │   │   ├── redis/
│   │   │   └── networking/
│   │   │
│   │   ├── 📁 environments/               # Environment configs
│   │   │   ├── dev/
│   │   │   │   └── terraform.tfvars
│   │   │   ├── staging/
│   │   │   │   └── terraform.tfvars
│   │   │   └── prod/
│   │   │       └── terraform.tfvars
│   │   │
│   │   └── 📁 scripts/
│   │       ├── apply.sh
│   │       ├── destroy.sh
│   │       └── validate.sh
│   │
│   ├── 📁 docker/                        # Docker configs
│   │   ├── docker-compose.yml            # Development
│   │   ├── docker-compose.prod.yml       # Production
│   │   │
│   │   ├── 📁 backend/
│   │   │   ├── Dockerfile                # Base image
│   │   │   ├── Dockerfile.dev
│   │   │   ├── Dockerfile.prod
│   │   │   └── .dockerignore
│   │   │
│   │   ├── 📁 frontend/
│   │   │   ├── Dockerfile
│   │   │   ├── Dockerfile.dev
│   │   │   ├── Dockerfile.prod
│   │   │   └── nginx.conf
│   │   │
│   │   ├── 📁 nginx/
│   │   │   ├── Dockerfile
│   │   │   ├── nginx.conf
│   │   │   └── ssl.conf
│   │   │
│   │   └── 📁 postgres/
│   │       ├── Dockerfile
│   │       └── init.sql
│   │
│   ├── 📁 ci-cd/                         # GitHub Actions workflows
│   │   ├── 📁 .github/workflows/
│   │   │   ├── backend-ci.yml            # Backend tests & build
│   │   │   ├── frontend-ci.yml           # Frontend tests & build
│   │   │   ├── mobile-ci.yml             # Mobile build
│   │   │   ├── deploy-staging.yml        # Deploy to staging
│   │   │   ├── deploy-prod.yml           # Deploy to prod
│   │   │   ├── security-scan.yml         # Security scans
│   │   │   └── performance-test.yml      # Performance tests
│   │   │
│   │   └── 📁 scripts/
│   │       ├── build.sh
│   │       ├── test.sh
│   │       ├── deploy.sh
│   │       └── rollback.sh
│   │
│   ├── 📁 monitoring/                    # Monitoring configs
│   │   ├── 📁 prometheus/
│   │   │   ├── prometheus.yml
│   │   │   └── rules.yml
│   │   │
│   │   ├── 📁 grafana/
│   │   │   ├── dashboards/
│   │   │   │   ├── kubernetes.json
│   │   │   │   ├── application.json
│   │   │   │   └── business_metrics.json
│   │   │   │
│   │   │   ├── datasources/
│   │   │   │   └── prometheus.yaml
│   │   │   │
│   │   │   └── provisioning/
│   │   │       └── dashboards.yaml
│   │   │
│   │   └── 📁 elk/
│   │       ├── elasticsearch.yml
│   │       ├── logstash.conf
│   │       └── kibana.yml
│   │
│   ├── 📁 backup/
│   │   ├── backup-postgres.sh
│   │   ├── backup-redis.sh
│   │   ├── restore-postgres.sh
│   │   └── s3-sync.sh
│   │
│   └── 📁 scripts/
│       ├── setup-cluster.sh
│       ├── setup-secrets.sh
│       ├── health-check.sh
│       └── maintenance.sh
│
└── 📁 .github/                           # GitHub config
    ├── ISSUE_TEMPLATE/
    │   ├── bug_report.md
    │   ├── feature_request.md
    │   └── question.md
    │
    ├── PULL_REQUEST_TEMPLATE/
    │   └── pull_request_template.md
    │
    └── workflows/                        # CI/CD workflows
        ├── backend-ci.yml
        ├── frontend-ci.yml
        └── deploy.yml
```

---

## Naming Conventions

### Django Apps
```
app_name/
├── __init__.py
├── models.py                    # Database models
├── views.py                     # API views
├── serializers.py               # DRF serializers
├── filters.py                   # Query filters
├── permissions.py               # Custom permissions
├── urls.py                      # URL routing
├── admin.py                     # Django admin
├── apps.py                      # App config
├── 📁 migrations/               # DB migrations
├── 📁 tests/                    # Tests
│   ├── test_models.py
│   ├── test_views.py
│   ├── test_serializers.py
│   └── conftest.py
└── 📁 management/
    └── commands/                # Custom management commands
```

### Frontend Components
```
// Pascal case for components
MyComponent.tsx
DataTable.tsx
UserProfile.tsx

// Hooks
useAuth.ts
useFetch.ts
useLocalStorage.ts

// Utils
formatDate.ts
validateEmail.ts
calculateTotal.ts

// Stores
authStore.ts
uiStore.ts

// Types
index.ts
api.ts
domain.ts
```

### Flutter
```
// Snake case for files
login_screen.dart
custom_button.dart
auth_provider.dart
date_utils.dart

// Class names (Pascal case)
class LoginScreen {}
class CustomButton {}
class AuthProvider {}
```

### Configuration Files
```
.env                             # Environment variables
.env.local                       # Local overrides (not committed)
.env.example                     # Example env file
.dockerignore                    # Docker ignore
.gitignore                       # Git ignore
.eslintrc.json                   # ESLint config
prettier.config.js               # Prettier config
tsconfig.json                    # TypeScript config
```

---

## File Size Guidelines

| File Type | Max Size | Reason |
|-----------|----------|--------|
| Component | 300 lines | Maintainability |
| Service | 400 lines | Single responsibility |
| Model | 200 lines | DDD principle |
| Serializer | 150 lines | Clarity |
| Test | 500 lines | Comprehensive coverage |
| View | 250 lines | REST endpoint |

---

## Import Organization

### Python
```python
# 1. Standard library
import os
import sys
from datetime import datetime

# 2. Third-party
import requests
from django.conf import settings
from rest_framework import serializers

# 3. Local
from shared.utils import decorators
from .models import Task
```

### TypeScript/JavaScript
```typescript
// 1. External packages
import React from 'react';
import { useRouter } from 'next/router';
import axios from 'axios';

// 2. Absolute imports
import { useAuth } from '@/hooks';
import { Button } from '@/components';

// 3. Relative imports
import { localService } from '../services';
import styles from './Component.module.css';
```

---

## Git Workflow

### Branch Naming
```
feature/user-authentication      # New feature
bugfix/login-error               # Bug fix
hotfix/critical-security-patch   # Production hotfix
refactor/api-serializers         # Refactoring
docs/architecture-update         # Documentation
```

### Commit Messages
```
feat(auth): add MFA support
fix(task): resolve duplicate task creation
docs(api): update endpoints documentation
test(gps): add location tracking tests
refactor(db): optimize query performance
chore(deps): update dependencies
```

---

## Environment Setup

### Development
```
.env.development
├── DEBUG=True
├── ALLOWED_HOSTS=localhost
├── DATABASE_URL=postgresql://...
├── REDIS_URL=redis://...
└── SECRET_KEY=dev-key
```

### Staging
```
.env.staging
├── DEBUG=False
├── ALLOWED_HOSTS=staging.example.com
├── DATABASE_URL=postgresql://...
└── SECURE_SSL_REDIRECT=True
```

### Production
```
.env.production
├── DEBUG=False
├── ALLOWED_HOSTS=example.com
├── DATABASE_URL=postgresql://...
├── SECURE_SSL_REDIRECT=True
└── SECURE_HSTS_SECONDS=31536000
```

---

## Documentation Structure

```
docs/
├── ARCHITECTURE.md              # System design
├── FOLDER_STRUCTURE.md          # This file
├── DATABASE_DESIGN.md           # Schema & ER
├── SERVICE_ARCHITECTURE.md      # Services specs
├── API_STRATEGY.md              # API design
├── SECURITY_STRATEGY.md         # Security
├── SCALABILITY_STRATEGY.md      # Performance
├── DEPLOYMENT_GUIDE.md          # Deployment steps
├── TROUBLESHOOTING.md           # Common issues
├── 📁 api/                      # API documentation
│   ├── auth.md
│   ├── tasks.md
│   ├── materials.md
│   ├── hr.md
│   ├── gps.md
│   └── dashboard.md
├── 📁 guides/                   # How-to guides
│   ├── local-setup.md
│   ├── database-setup.md
│   ├── deployment.md
│   └── troubleshooting.md
└── 📁 architecture/             # Architecture docs
    ├── microservices.md
    ├── data-model.md
    ├── security.md
    └── performance.md
```

Ready to implement! 🚀
