helm template .
helm package .


helm install myhelm ./my-app-1.0.0.tgz  >>> release myhelm will be deployed in default namespace and within that, it resource will be deployed in the respective mentioned ns.

helm install myhelm ./my-app-1.0.0.tgz -n deepak  >>> this will install release in ns deepak, where all resources are going to get deployed.

helm list -A
helm uninstall myhelm

helm upgrade myhelm ./my-app-1.0.1.tgz >>>> upgrade existing release with new package

helm upgrade --install release1 . -f ../values/dev-values.yaml
helm history release1 -n default
helm get manifest release1 -n default --revision 2
helm get values release1 -n default --revision 2


Create new helm release with new values.yaml and using the same package >>

helm install my-app-prod ./my-app-1.0.0.tgz --values dev-values.yaml

----------------------------------------------------------------------------------
----------------------------------------------------------------------------------

Always keep a .helmignore in your charts to prevent accidental inclusion of large or sensitive files.

Ignore *.tgz so previously packaged charts aren’t nested inside new packages.

Keep environment-specific values files (dev-values.yaml, staging-values.yaml) out of the chart and store them in your CI repo/environment or a values-bucket/secret store.

----------------------------------------------------------------------------------
----------------------------------------------------------------------------------

Environment-specific values files (dev-values.yaml, staging-values.yaml, prod-values.yaml) SHOULD NOT live inside the chart directory.
They should live outside the chart — usually next to the chart or in a separate repo — and you pass them during helm install or helm upgrade.

my-app/
  chart/
    Chart.yaml
    templates/
    values.yaml
  values/
    dev.yaml
    prod.yaml




helm install my-app ./my-app/chart -f ./my-app/values/dev.yaml

