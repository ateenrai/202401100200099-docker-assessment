# Docker & Container Security — Practical Assessment

## Personal details

- Name: Not provided
- Registration number: `202401100200099`
- PORT: `179` (`80 + 99`)
- Docker Hub username: Not provided
- Docker Hub repository: Not created; username and authenticated publishing are required.
- Required GitHub repository name: `202401100200099-docker-assessment`
- GitHub URL: Not created or verified.

## Project

FestPass consists of a Flask registration API, an Nginx frontend, and a
PostgreSQL database. The Compose configuration puts the frontend and backend
on one network and the backend and database on a separate internal network.
PostgreSQL data is stored in the `postgres-data` named volume.

Copy `.env.example` to `.env` and replace `DB_PASSWORD` with a strong random
value before starting the Compose stack. `.env` is ignored by Git. Never commit
it, passwords, access tokens, or signing private keys.

The backend Dockerfile currently uses the pinned Python `3.13.9-slim-bookworm`
base, installs pinned application dependencies before copying the application,
and runs as UID/GID `10001`. This is the intended hardened Stage 3 image
configuration; the required Docker build and vulnerability scan have not been
run in this environment.

## Verification status

| Check | Result |
|---|---|
| Backend Python syntax (`python -m py_compile backend/app.py`) | Passed |
| Docker daemon | Not available: Docker Desktop reports that it is unable to start; WSL is not installed |
| Docker build, Compose startup, API, database persistence, and network isolation | Not run |
| Trivy scans and CRITICAL/HIGH counts | Not run; no scan results are claimed |
| Image sizes | Not available; no images were built |
| Docker Hub push, published digest, and registry deployment | Not run; Docker Hub username/authentication unavailable |
| Cosign key generation, signing, and signature verification | Not run; Cosign is unavailable |
| Git commit | Initial commit created locally; GitHub push not run |

`reports/trivy-before.txt` and `reports/trivy-after.txt` are status notes, not
scanner output. Replace them with genuine Trivy output after running the
required scans. The before/after counts and image sizes must be added here from
those actual runs.

## Required evidence still to capture

Capture genuine, unedited screenshots on this machine with the registration
number in the PowerShell prompt. No screenshots or test output have been
fabricated.

| Evidence | Status |
|---|---|
| S1-2, S1-3 | Not captured; Docker daemon unavailable |
| S2-2, S2-3, S2-4 | Not captured; Docker daemon unavailable |
| S3-1, S3-3 | Not captured; Trivy/Docker unavailable |
| S4-1, S4-2, S4-3 | Not captured; Docker Hub username/authentication unavailable |
| S5-1, S5-2, S5-3, S5-4 | Not captured; Cosign/Docker Hub unavailable |

## AI tools

- GitHub Copilot in VS Code: used to prepare the project files and explain the
  setup blockers. Commands that require Docker, Trivy, Cosign, GitHub, or
  Docker Hub have not been represented as successfully run.

## Incomplete tasks

- Install WSL from an elevated PowerShell (`wsl --install`) and restart
  Windows; start Docker Desktop and confirm `docker version` shows a Server.
- Install/verify Git, Trivy, and Cosign. Download the Trivy database and pull
  the assessment's required base images.
- Run the original Stage 1 `python:3.9` build and capture S1-2/S1-3 before
  recording those historical results; the current Dockerfile is the hardened
  Stage 3 version.
- Create `.env` locally from `.env.example` with a strong database password,
  run the stack, exercise both registrations, network isolation, and volume
  persistence.
- Run both genuine Trivy scans and the CRITICAL gate; replace the report status
  notes and record measured vulnerability counts and image sizes.
- Provide a Docker Hub username, authenticate with Docker's normal login flow,
  publish tags `1.0.0` and `1.0`, and record the actual digest.
- Generate a password-protected Cosign key pair locally, keep `cosign.key`
  private and uncommitted, commit the generated `cosign.pub`, sign the actual
  `1.0.0` digest, and demonstrate verification success and unsigned `1.0.1`
  rejection.
- Capture all required screenshots, create the public GitHub repository named
  `202401100200099-docker-assessment`, commit each stage separately, review
  the changes, and push only after approval.
