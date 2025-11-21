# DADAFA React Application

A simple React application that displays "DADAFA" centered on the screen with a cyan glow effect.

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
You may also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can't go back!**

If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own.

You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)

---

## DADAFA Project Deployment

### Infrastructure Setup

This application is designed to be deployed via Terraform and GitHub Actions to AWS CloudFront + S3, following the same pattern as `transcribe.cloudlords.com`.

### Prerequisites

1. **GitHub Repository**: Must be created via Terraform first (infrastructure-automation repo)
2. **AWS Infrastructure**: S3 bucket, CloudFront distribution, and domain configuration
3. **GitHub Actions**: CI/CD pipeline for automated deployment

### Deployment Steps (After Terraform Setup)

Once the Terraform infrastructure is in place and the GitHub repository is created:

1. **Add GitHub remote**:
   ```bash
   git remote add origin https://github.com/shaddar91/DADAFA.git
   ```

2. **Push to GitHub**:
   ```bash
   git push -u origin master
   ```

3. **Automatic Deployment**: GitHub Actions will automatically:
   - Build the React application (`npm run build`)
   - Deploy build artifacts to S3
   - Invalidate CloudFront cache
   - Make the app available at: `https://dada.cloud-lord.com`

### Infrastructure Components

- **Frontend**: React 19.2.0 (this repository)
- **Hosting**: AWS S3 + CloudFront
- **Domain**: https://dada.cloud-lord.com
- **S3 Bucket**: personal-dada-544587720954
- **CloudFront Distribution**: d1yx04rakb3oan.cloudfront.net
- **CI/CD**: GitHub Actions
- **IaC**: Terraform (from infrastructure-automation repository)

### Application Features

- **Centered Display**: Large "DADAFA" text in the center of the screen
- **Modern Styling**: Cyan color (#61dafb) with glowing text shadow effect
- **Responsive Design**: Works on all screen sizes
- **Dark Theme**: Dark background (#282c34)

### Tech Stack

- React 19.2.0
- Create React App 5.0.1
- CSS3 for styling
- Node.js v20.10.0

### GitHub Actions OIDC Authentication

The deployment uses **OpenID Connect (OIDC)** for secure AWS authentication without storing access keys:

- **IAM Role ARN**: arn:aws:iam::544587720954:role/personal-dada-github-actions-role
- **AWS Region**: eu-central-1
- **GitHub Username**: Shaddar91 (case-sensitive!)
- **Repository**: dada-fa

**Important Notes:**
- Username capitalization matters: `Shaddar91` (capital S, capital second letter)
- Secrets are automatically managed by Terraform
- No AWS access keys required in GitHub repository settings

### Troubleshooting

**GitHub Actions Build Failure**: If deployment fails with "Cannot find directory", check:
1. GitHub Actions workflow uses correct build directory:
   - Create React App → `build/` directory
   - Vite → `dist/` directory
2. Build command matches package.json scripts
3. OIDC role assumption succeeds (check IAM trust policy)

---

**Generated**: 2025-11-21
**Last Updated**: 2025-11-21
**Part of**: Personal Projects Infrastructure
