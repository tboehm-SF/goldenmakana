# Makana Health Website

Official website for Makana Health - an integrated clinical ecosystem for healthcare professionals and patients.

## Overview

Makana Health offers innovative medicines across multiple therapeutic areas:
- Cardiovascular
- Immunology  
- Neuroscience
- Oncology

The website features dual-portal access for both healthcare professionals (HCP Portal) and patients (Patient Portal).

## Features

- **HCP Portal**: Clinical records, e-prescriptions, trial finder
- **Patient Portal**: Appointments, messaging, patient stories
- **Product Showcase**: Information about approved and pipeline medicines
- **AI Assistant**: Powered by Agentforce
- **Clinical Resources**: Knowledge base and clinical trial information

## Technology Stack

- Static website with JavaScript
- Netlify Functions for backend services
- AES-256 encryption for secure portal access
- HIPAA-compliant infrastructure

## Deployment

This site is deployed on Netlify with automatic deployments from the `main` branch.

### Netlify Configuration

See `netlify.toml` for build settings, redirects, and security headers.

### Environment Variables

Required environment variables (set in Netlify dashboard):
- API keys and tokens (if applicable)
- Backend service URLs

## Development

To run locally:
```bash
# Install dependencies (if using a build tool)
npm install

# Serve locally
npx serve .
```

## Contact

For questions about Makana Health, visit [goldenmakana.netlify.app](https://goldenmakana.netlify.app)

---

🤖 Repository setup with Claude Code
