1. Create projects:
```
oc new-project dev-practicetest
oc new-project test-practicetest
oc new-project prd-practicetest
oc new-project tools-practicetest
```

2. Create environments
```
oc apply -k environments/overlays/dev
oc apply -k environments/overlays/test
oc apply -k environments/overlays/prod
```

3. Validate all environments are running

4. Create secrets/.dockerconfigjson file

4. Create pipelines:
```
oc apply -k environments/overlays/tools
```

5. Link docker secret to pipeline SA:
```
oc secrets link pipeline docker-registries -n tools-practicetest
```

6. Apply rolebindings to enable pipeline serviceaccount to deploy in other apps:
```
oc apply -k components/rbac/base
```