# E-Sante Platform

A multi-application healthcare platform for patients, doctors, and administrators. It combines a Flutter mobile application, a Next.js administration panel, and a set of Node.js services for healthcare workflows.

## Platform Components

```text
esante_app/      Flutter application for patients and healthcare professionals
admin-e-sante/  Next.js administration dashboard
backend/         API gateway and domain services
docs/            Architecture and project documentation
```

## Main Capabilities

- Authentication and user profiles
- Appointment scheduling and management
- Medical records and referrals
- Messaging and notifications
- Ratings, administration, and audit trails
- Service discovery and API gateway routing

## Tech Stack

- Flutter and Dart
- Next.js, TypeScript, Tailwind CSS, and Prisma
- Node.js service architecture
- Consul-based service configuration

## Getting Started

Read [TESTING_GUIDE.md](TESTING_GUIDE.md) for the current local testing workflow. On Windows, `start_services.bat` can start the configured backend services after their dependencies and environment values are installed.

For individual components:

```bash
cd admin-e-sante
npm install
npm run dev
```

```bash
cd esante_app
flutter pub get
flutter run
```

Each backend service has its own runtime configuration. Keep database URLs, tokens, and third-party credentials in local environment files rather than source control.
