# Tequendama Theme for Ghost

![Sass Build](https://github.com/cdvel/tequendama/workflows/Sass%20Build/badge.svg)
![Ghost v4.x Compatible](https://img.shields.io/badge/Ghost%20v4.x-Compatible-brightgreen.svg)

--- 

A Ghost theme for my personal blog

## Development

### Compile this theme manually

```bash
sass -t compressed assets/css/styles.scss assets/css/styles.css
```

### Workflow Overview

This theme uses GitHub Actions to:
1. Compile SCSS files to CSS
2. Deploy changes to a staging branch (`pr-pages`)
3. Automatically deploy to the production server

## Installation & Migration

### Manual Installation

Follow this guide: [Installing Ghost 1.0 without Ghost CLI](https://nehalist.io/installing-ghost-1-0-without-ghost-cli/)

### Migration Steps

For migrating to Ghost 1.0.0, follow: [Migration Guide](https://docs.ghost.org/docs/migrating-to-ghost-1-0-0#section-4-copy-your-images)

### Theme Updates

Validated for 4.X using [GScan](https://gscan.ghost.org/)

## Repository Structure

- `src-pages`: Source branch containing SCSS files
- `pr-pages`: Automated build branch with compiled CSS
- `assets/css`: Contains both source SCSS and compiled CSS files
- `partials`: Theme template partials
- `static`: Static theme assets

## Deployment

Changes to the `src-pages` branch automatically trigger the build and deployment workflow.

### Manual Deployment

If you need to deploy manually, follow the workflow steps in the GitHub Actions file.

## Manual Update to Latest Ghost

Run these commands from your home directory:

```bash
# Download and extract latest Ghost version
curl -LOk https://ghost.org/zip/ghost-latest.zip
unzip ghost-latest.zip -d ghost-temp

# Remove old files
sudo rm -rf /opt/ghost/core
sudo rm /opt/ghost/index.js
sudo rm /opt/ghost/*.json
sudo rm /opt/ghost/*.md

# Copy new files
sudo cp -R ~/ghost-temp/core /opt/ghost/
sudo cp -R ~/ghost-temp/index.js /opt/ghost/
sudo cp -R ~/ghost-temp/package.json /opt/ghost/
sudo cp -R ~/ghost-temp/npm-shrinkwrap.json /opt/ghost/
sudo cp -R ~/ghost-temp/*.md /opt/ghost/
sudo chown -R ghost:ghost /opt/ghost

# Install dependencies and set permissions
sudo npm install --production
sudo chown -R ghost:ghost /opt/ghost

# Restart service
service nginx restart
```

## Troubleshooting

If `npm install` fails, try upgrading npm:

```bash
sudo npm install -g npm
```

### Common Issues

- If CSS changes aren't visible, check if the workflow completed successfully
- For deployment issues, verify SSH credentials and server configuration
