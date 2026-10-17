# YadetApp

YadetApp is a business management platform for automotive service businesses. It helps service providers manage their business operations and customer relationships, while customers can access their own services and information through a dedicated experience.

The application has three user roles, each with its own permissions and dedicated panel:

- **Admin** — manages and oversees the platform.
- **Service Provider** — manages automotive service business operations and customer interactions.
- **Customer** — accesses customer-facing features and their own service information.

The platform is built with Django, Next.js, Redis, and PostgreSQL. The web application is designed as a Progressive Web App (PWA), with Android APK packaging planned through the PWA delivery approach.

## Features

- Role-based access for administrators, service providers, and customers.
- Separate panels and permissions for each role.
- Business management workflows for automotive service providers.
- Customer relationship and service-history workflows.
- Responsive web experience.
- PWA-oriented architecture for app-like use on supported devices.
- Android APK distribution planned through a PWA packaging solution.

> Specific business features depend on the modules enabled in the current version.

## Technology Stack

| Component | Technology | Purpose |
| --- | --- | --- |
| Backend | Django | Business logic, authentication, permissions, and APIs |
| Frontend | Next.js | Web interface and role-specific panels |
| Cache / supporting services | Redis | Caching and other asynchronous or transient workloads as configured |
| Database | PostgreSQL | Persistent application data |
| Mobile delivery | PWA → APK | Package the web experience for Android distribution |

## User Roles

### Admin

The admin panel is intended for platform-level management and administrative operations. Access is restricted to authorized administrator accounts.

### Service Provider

The service-provider panel is intended for automotive businesses and their service workflows. Its permissions are scoped to the provider's authorized business data and operations.

### Customer

The customer panel provides customers with access to customer-facing functionality and their own information. Customers should not be able to access other customers' private data or provider-only management features.

Role permissions should be enforced by the backend, not only by hiding or showing frontend pages.

## Architecture

At a high level:

```text
User
 |
 v
Next.js Web App (PWA)
 |
 v
Django Backend / API
 |             |
 v             v
PostgreSQL    Redis
```

- **Next.js** serves the user interface and role-specific panels.
- **Django** enforces business rules, authentication, authorization, and API behavior.
- **PostgreSQL** stores persistent application data.
- **Redis** supports caching and any configured background or transient workloads.
- **PWA packaging** provides an app-like installation experience and can be used as the basis for Android APK distribution.

## Development Setup

The exact commands depend on the repository layout and the project's environment configuration. In a typical development environment, you will need:

- Python and the project's supported Django dependencies.
- Node.js and the package manager used by the frontend.
- PostgreSQL.
- Redis.
- Environment variables for database access, Django settings, API URLs, and other required services.

### Backend

Install the Python dependencies using the dependency manager or requirements file provided by the backend project, configure the environment variables, apply database migrations, and start the Django development server.

Example for a project that uses `requirements.txt`:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

### Frontend

Install the dependencies using the package manager specified by the frontend lockfile, configure the backend API URL, and start the Next.js development server.

For an npm-based project:

```bash
npm install
npm run dev
```

These are typical commands; use the scripts and dependency files in the actual repositories if they differ.

## PWA and Android APK

YadetApp is intended to be delivered as a Progressive Web App. A PWA can provide an installable, app-like experience in supported browsers.

For Android distribution, the PWA can be packaged as an APK using an appropriate packaging workflow, such as a Trusted Web Activity where the domain and web application meet the requirements. APK generation, signing, and distribution should be configured as part of the release process.

The PWA and APK must still rely on the backend for authoritative authentication, permissions, and business operations.

## Configuration and Security

- Keep secrets in environment variables or an appropriate secrets manager.
- Do not commit production credentials, private keys, tokens, or `.env` files.
- Enforce role-based permissions in Django APIs.
- Validate and authorize access to business and customer records on the server.
- Use HTTPS in deployed environments.
- Configure CORS, trusted hosts, cookies, and authentication settings for the deployment environment.
- Use database backups and appropriate Redis persistence/configuration according to operational requirements.
- Review dependencies and deployment settings before production releases.

## Project Status

YadetApp is being developed as a management platform for automotive businesses. The architecture includes a Django backend, Next.js frontend, Redis, PostgreSQL, and a PWA-based approach to Android APK delivery.

## License

Add the project's license here when it has been selected.
