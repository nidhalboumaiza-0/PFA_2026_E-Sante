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

## Run Locally

1. Install Docker Desktop, Node.js 18 or newer, Flutter, and an Android development toolchain. Start Docker Desktop and verify the tools:

   ```bash
   docker --version
   docker compose version
   node --version
   flutter doctor
   ```

2. Configure the backend from the repository root:

   ```powershell
   cd backend
   Copy-Item .env.example .env
   ```

   On macOS or Linux, use `cp .env.example .env`. Replace the sample JWT and optional email, storage, and Firebase values in `backend/.env`.

3. Build and start MongoDB, Redis, Kafka, Consul, the eight services, and the API gateway:

   ```bash
   docker compose up -d --build
   ```

4. Wait for the containers to become healthy, then verify the gateway:

   ```bash
   docker compose ps
   curl http://localhost:3000/health
   ```

5. Start the administration panel in a second terminal:

   ```bash
   cd admin-e-sante
   npm install
   ```

6. Create `admin-e-sante/.env.local`, initialize its local SQLite database, and run Next.js:

   ```dotenv
   DATABASE_URL=file:./dev.db
   ```

   ```bash
   npm run db:generate
   npm run db:push
   npm run dev
   ```

   Open `http://localhost:3010`.

7. The Flutter client already targets `http://10.0.2.2:3000` for an Android emulator. For a physical phone, replace that address in `esante_app/lib/injection_container.dart` and the two WebSocket service files with the computer's LAN IP.
8. Start the mobile application in a third terminal:

   ```bash
   cd esante_app
   flutter pub get
   flutter devices
   flutter run
   ```

9. Stop the backend when finished:

   ```bash
   cd backend
   docker compose down
   ```

See [TESTING_GUIDE.md](TESTING_GUIDE.md) for health checks and test scenarios. Keep database URLs, tokens, and third-party credentials out of source control.
