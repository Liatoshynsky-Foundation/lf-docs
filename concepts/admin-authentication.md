# Admin Authentication

The authentication feature provides secure, session-based access to the admin panel.

Only pre-registered administrator accounts can access the admin panel. Administrator accounts are created directly in the system by a developer. Self-registration and public sign-up are not supported.

All administrators have the same level of access. Role-based access control and administrator role hierarchy are not included in the current scope.

## Authentication

Administrators sign in using their registered email address and password.

Passwords are stored securely as hashes and never as plain text.

Access to all admin panel routes is protected server-side. Unauthenticated requests are redirected to the login page regardless of how the protected route is accessed.

Authenticated sessions remain active until the administrator:

- logs out; or
- remains inactive for the configured period and the session expires.

After the session expires, the administrator must sign in again.

## Login Protection

Repeated failed login attempts are limited to reduce the risk of brute-force attacks. Further login attempts are temporarily blocked after the configured threshold is reached.

Authentication-related forms use CSRF protection.

## Password Reset

Administrators can reset their password using their registered email address.

Password reset links are:

- unique;
- time-limited;
- valid for one use only.

Password reset requests are rate-limited to prevent abuse.

The password reset flow does not reveal whether an email address is registered. The same confirmation message is displayed for both registered and unrecognized email addresses.

## Password Requirements

Passwords must meet the following requirements:

- Minimum length: 10 characters
- At least one uppercase letter
- At least one number
- At least one special character, such as `!@#$%`

The password requirements are intended to provide an appropriate level of protection without making password creation unnecessarily complicated for administrators.

Additional restrictions, such as prohibiting repeated characters or requiring periodic password changes, are not applied.

> **UI text:** Пароль має містити щонайменше 10 символів, включаючи велику літеру, цифру та спеціальний символ (наприклад, !@#$%).

## Login Flow

1. The administrator opens `/admin/login`.
2. The login page displays:
   - **Email** field
   - **Password** field
   - **Увійти** button
   - **Забули пароль?** link
3. The administrator enters the registered email address and password and submits the form.
4. The credentials are validated.
5. If the credentials are valid:
   - an authenticated session is created;
   - the administrator is redirected to the admin panel dashboard;
   - protected admin panel routes become accessible.
6. The administrator can begin working in the admin panel.

## Out of Scope

The following capabilities are not included in the current implementation:

- Multi-factor authentication (MFA)
- OAuth authentication
- Audit logging
- Self-registration
- Role-based access control (RBAC)

These capabilities may be considered in the future if the Foundation's requirements change.