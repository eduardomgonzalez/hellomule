# Hello Mule Baseline

## Environment
- Anypoint Studio: 7.22
- Mule runtime local: Mule Server 4.10.0 EE
- Java: 17
- Workspace: `C:\Users\edgonzalez\AnypointStudio\studio-workspace`
- Project: `hellomule`

## Local Endpoints
- `GET http://localhost:8081/hellomule`
- `GET http://localhost:8081/health`

## CloudHub Endpoint
- Base URL: `https://hellomule-t9l084.5sc6y6-1.usa-e2.cloudhub.io`
- `GET /hellomule`

## Baseline Validation
- Local deploy reached `DEPLOYED`.
- Postman returned `200 OK` for `/hellomule`.
- CloudHub 2.0 deploy reached `Running`.
- Public CloudHub endpoint returned `200 OK`.

## Notes
- Deploy menu appeared from `Package Explorer`, not `Project Explorer`.
- Runtime Manager target used `CloudHub 2.0` in the `SANDBOX` environment.
