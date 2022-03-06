# ocp3-4-stateless-cicd



## Steps
- Authorize Jenkins to deploy onto OCP 4 cluster 
      oc project dev
      oc create sa jenkins-user
      oc adm policy add-cluster-role-to-user edit -z jenkins-user
      oc describe sa jenkins-user
      oc describe secret jenkins-user-token-xxxx
- Extend Jenkins pipeline to deploy the stateless nodejs app onto OCP 4
    oc new-project dev --display-name="Tasks - Dev"
    oc new-project cicd --display-name="CI/CD"

    # Grant Jenkins Access to Projects
    oc policy add-role-to-group edit system:serviceaccounts:cicd -n dev
    oc new-app -n cicd -f cicd-template.yaml


