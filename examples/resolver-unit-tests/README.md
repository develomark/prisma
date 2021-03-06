# resolver-unit-tests

This example demonstrates how to unit test GraphQL resolvers using [`graphql-yoga`](https://github.com/prismagraphql/graphql-yoga), a Prisma test instance on [Travis CI](https://travis-ci.com/) and [jest](https://github.com/facebook/jest).

## Get started

> **Note**: The project setup in this example is minimalistic. You can use it as a reference example for your own project, but you might want to evolve it into a more advanced setup. For example, you can use [encrypted environment variables](https://docs.travis-ci.com/user/environment-variables/#Defining-encrypted-variables-in-.travis.yml) for sensitive information like the Prisma API secret.

### 1. Download the example

Clone the Prisma monorepo and navigate to this directory or download _only_ this example with the following command:

```sh
curl https://codeload.github.com/prismagraphql/prisma/tar.gz/master | tar -xz --strip=2 prisma-master/examples/resolver-unit-tests
```

### 2. Set up repository locally and on GitHub

Next, navigate into the downloaded folder and initiate a new git repository:

```sh
cd resolver-unit-tests
git init .
```

In your GitHub account, create a new repository and copy its git URL, for example:

`git@github.com:marktani/resolver-unit-tests.git`

Add a new remote to your local git repository:

```sh
git remote add origin git@github.com:marktani/resolver-unit-tests.git
```

### 3. Link GitHub and Travis CI

Now, link your GitHub account in your [Travis CI](https://travis-ci.com/) account, and push the downloaded example to your repository:

```sh
git push --set-upstream origin master
```

### 4. Verify the build

In your Travis CI account, review the build and confirm that the build went through.

Here is a description of the performed steps that are expected to happen (compare to `.travis.yml` as well):

1.  We install the `npm` dependencies with `npm install`.
2.  We spin up a new Prisma server and database using `docker-compose up -d`.
3.  We confirm that the Docker setup is correct with `docker ps`.
4.  We sleep 20 seconds to allow for the two Docker containers to finish their setup.
5.  We run `prisma deploy` with the locally installed version of Prisma. This will set up a new service `travis` at stage `test`.
6.  We run `npm run test` to execute the `jest` test suite.
