<p align="center"><a href="https://nx1.io" target="_blank"><img src="https://assets-global.website-files.com/64c733db66ebf722f72bea5f/659b56a81b3593da28afb1f0_nx1-logo.svg" width="400" alt="NX1.io"></a></p>


# Documentation for NX1 Deploy - App GitHub Workflow

## Overview
This GitHub workflow is designed for deploying an ExpressJS application using the NX1 platform. It is triggered manually and performs a series of steps to prepare, assume the necessary role, and deploy the ExpressJS application to a specified environment.

## Workflow Name

**Name**: NX1 Deploy - ExpressJS App
Run Name: This workflow will be logged as "Deploy example-expressjs-app to my environment by @<github_actor>" in the GitHub actions tab, where <github_actor> is the username of the person who triggered the run.

## Trigger

**Manual (workflow_dispatch)**: This workflow is triggered manually. It does not run automatically on any code push or pull request event. It needs to be manually dispatched from the GitHub Actions tab in the repository.

## Permissions

**id-token**: write: This workflow requires permissions to write an ID token for authentication purposes.

contents: read: It also requires read access to the repository contents.

## Jobs

### Deploy

This job runs on the latest Ubuntu runner and consists of several steps:

#### 1.**Checkout code**:

- Action: actions

Purpose: Checks out the repository code, allowing the workflow to access it.

#### 2.**NX1 Prepare Deployment**:

- Action: Prepare
- With:

    - operation: 'prepare'

    - app_id: The application ID.**Do not modify it**.

    - env_id: The environment ID where the app will be deployed.**Do not modify it**. 

    - api_token: An API token for authentication, stored in GitHub secrets. Create your api_token on [NX1.io app](https://app.nx1.io/) or read the [documentation](https://docs.nx1.io/).

Purpose: Prepares the deployment environment for the ExpressJS app using the NX1 platform.

#### 3.**NX1 Assume Role**:

- Action: `nx1-io/app-copilot-action@main`
- With:
    - operation: 'assume-role'

Purpose: Assumes the necessary role for deployment.

#### 4.**NX1 Deploy Service - expressjs-app**:

- Action: `nx1-io/app-copilot-action@main`
- With:

    - operation: 'deploy'

    - service: 'expressjs-app' (the name of the service to be deployed -**define it on NX1.io app**)

Purpose: Deploys the ExpressJS application to the specified environment.

### Additional Notes

**Version**: This document corresponds to the first revision of the workflow (rev:1).

**Security**: The workflow uses a secret (NX1_API_TOKEN) for the API token, ensuring security and confidentiality.

**Customization**: To adapt this workflow for different applications or environments, modify the api_token.


<hr/>


<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

You may also try the [Laravel Bootcamp](https://bootcamp.laravel.com), where you will be guided through building a modern Laravel application from scratch.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains over 2000 video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the [Laravel Partners program](https://partners.laravel.com).

### Premium Partners

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[WebReinvent](https://webreinvent.com/)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Curotec](https://www.curotec.com/services/technologies/laravel/)**
- **[Cyber-Duck](https://cyber-duck.co.uk)**
- **[DevSquad](https://devsquad.com/hire-laravel-developers)**
- **[Jump24](https://jump24.co.uk)**
- **[Redberry](https://redberry.international/laravel/)**
- **[Active Logic](https://activelogic.com)**
- **[byte5](https://byte5.de)**
- **[OP.GG](https://op.gg)**

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
