# Contentstack Kickstart: Next.js

Contentstack Kickstarts are the minimum amount of code needed to connect to Contentstack.
This kickstart covers the following items:

- SDK initialization
- Live preview and Visual building setup
- Support for standard regions (EU/US) and development regions with automatic endpoint generation

More details about this codebase can be found on the [Contentstack docs](https://www.contentstack.com/docs/developers).

[![Join us on Discord](https://img.shields.io/badge/Join%20Our%20Discord-7289da.svg?style=flat&logo=discord&logoColor=%23fff)](https://community.contentstack.com)

## How to get started

Before you can run this code, you will need a Contentstack "Stack" to connect to.
Follow the following steps to seed a Stack that this codebase understands.

> If you installed this Kickstart via the Contentstack Markertplace or the new account onboarding, you can skip this step.

### Install the CLI

```bash
npm install -g @contentstack/cli
```

### Log in via the CLI

```bash
csdx auth:login
```

### Get your organization UID

In your Contentstack Organization dashboard find `Org admin` and copy your Organization ID (Example: `blt481c598b0d8352d9`).

### Create a new stack

Make sure to replace `<YOUR_ORG_ID>` with your actual Organization ID and run the below.

```bash
csdx cm:stacks:seed --repo "contentstack/kickstart-stack-seed" --org "<YOUR_ORG_ID>" -n "Kickstart Stack"
```

## Create a new delivery token.

Go to `Settings > Tokens` and create a delivery token. Select the `preview` scope and turn on `Create preview token`

## Fill out your .env file.

Now that you have a delivery token, you can fill out the .env file in your codebase.

> You can find the API key, Delivery Token and Preview Token in Settings > Tokens > Your token.

```
NEXT_PUBLIC_CONTENTSTACK_API_KEY=<YOUR_API_KEY>
NEXT_PUBLIC_CONTENTSTACK_DELIVERY_TOKEN=<YOUR_DELIVERY_TOKEN>
NEXT_PUBLIC_CONTENTSTACK_PREVIEW_TOKEN=<YOUR_PREVIEW_TOKEN>
NEXT_PUBLIC_CONTENTSTACK_REGION=<YOUR_REGION>
NEXT_PUBLIC_CONTENTSTACK_ENVIRONMENT=preview
NEXT_PUBLIC_CONTENTSTACK_PREVIEW=true
```

### Development Regions Support

This implementation now supports development regions with automatic endpoint generation. To use a development region:

1. Set `NEXT_PUBLIC_CONTENTSTACK_REGION` to your development region identifier (e.g., `dev11`, `dev14`, `stag`)

The system will automatically generate the necessary endpoints using the following pattern:
- API Host: `https://{region}-api.csnonprod.com`
- App Host: `https://{region}-app.csnonprod.com`
- Preview Host: `https://{region}-rest-preview.csnonprod.com`

Examples:
```
# For dev11
NEXT_PUBLIC_CONTENTSTACK_REGION=dev11
# Automatically generates:
# - https://dev11-api.csnonprod.com
# - https://dev11-app.csnonprod.com
# - https://dev11-rest-preview.csnonprod.com

# For stag
NEXT_PUBLIC_CONTENTSTACK_REGION=stag
# Automatically generates:
# - https://stag-api.csnonprod.com
# - https://stag-app.csnonprod.com
# - https://stag-rest-preview.csnonprod.com
```

For standard regions (EU/US), the system will use the default Contentstack endpoints.

## Turn on Live Preview

Go to Settings > Live Preview. Click enable and select the `Preview` environment in the drop down. Hit save.

## Install the dependencies

```bash
npm install
```

### Run your app

```bash
npm run dev
```

### See your page visually

### In the browser

Go to `http://localhost:3000`.

#### In the CMS

Go to Entries and select the only entry in the list.
In the sidebar, click on the live preview icon.
Or, see your entry in the visual builder
