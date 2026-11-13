# INC-001 — Nginx configuration failure

## Symptom
Nginx failed configuration validation and could not start correctly.

## Detection
The issue was detected with:

`sudo nginx -t`

Error pointed to an unknown directive in `/etc/nginx/nginx.conf`.

## Root cause
Invalid characters were accidentally introduced into the Nginx configuration.

## Resolution
The invalid configuration line was corrected.

Validation:

`sudo nginx -t`

Then the service was restarted:

`sudo systemctl restart nginx`

## Verification
- `systemctl status nginx`
- `curl localhost`
- `ss -lntp | grep :80`

The service returned to `active (running)` and HTTP traffic was restored.

## Lesson learned
Validate Nginx configuration before restart and use the error message to identify the exact file and line.
