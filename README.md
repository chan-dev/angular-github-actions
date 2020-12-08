# AngularGithubActions

This is a simple repo based on this [tutorial](https://focisolutions.com/2020/04/github-actions-deploying-an-angular-app/) that shows how to use github actions with [Angular](Angular)

Make sure to rename the main branch as `main` and update the
`.github/workflow/main.yml` accordingly.

We need to do something differently from the tutorial.
We have to use `GabrielBB/xvfb-action@v1` action for tests to run in github
actions.

So replace this part from the `build` job:
```
- name: Test
  run: npm run test:ci
```

with
```
- name: Run headless test
  uses: GabrielBB/xvfb-action@v1
  with:
    working-directory: ./ #optional
    run: npm run test:ci
```
