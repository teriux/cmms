# CMMS OTMV Architecture Documentation

## Overview
This project follows a **Feature-First Clean Architecture** approach. This ensures scalability, testability, and separation of concerns.

## Directory Structure
The `lib` folder is the core of the application:

### `core/`
Contains shared logic and utilities used across multiple features.
- **constants**: Assets paths, API endpoints, static strings.
- **error**: Custom `Failure` classes and exception handlers.
- **network**: HTTP clients (e.g., Dio), interceptors, connectivity checks.
- **theme**: Application theme definitions (colors, text styles).
- **utils**: Helpher functions (date formatting, validators).
- **widgets**: Generic, reusable UI components (Buttons, Input fields).

### `config/`
Global configuration.
- **routes**: Navigation setup (GoRouter).
- **localization**: Internationalization setup.

### `features/`
Each feature (module) is self-contained with its own Clean Architecture layers:
- **[feature]/data**:
    - `datasources`: API calls, local database access.
    - `models`: DTOs (Data Transfer Objects) that parse JSON.
    - `repositories`: Implementation of domain repositories.
- **[feature]/domain**:
    - `entities`: Pure Dart classes representing data.
    - `repositories`: Abstract interfaces defining data operations.
    - `usecases`: Business logic encapsulating single actions.
- **[feature]/presentation**:
    - `pages/screens`: The UI views.
    - `widgets`: Feature-specific widgets.
    - `bloc/provider`: State management logic.

## Modules Implemented
- **auth**: Authentication (Login, Register, Role management).
- **organizations**: Management of Organizations, Buildings, Locations.
- **inventory**: Asset management (Systems, Equipment, Components).
- **planning**: Scheduler and planning tools.
- **work_orders**: OTMV (Virtual Work Orders) execution and templates.
- **logistics**: Parts and services management.
- **dashboard**: Main landing/overview page.

## State Management
(Recommended: BLoC or Riverpod) - *To be decided/implemented based on preference.*
