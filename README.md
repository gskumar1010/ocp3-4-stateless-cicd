# ocp3-4-stateless-cicd



## Steps
- Authorize Jenkins to deploy onto OCP 4 cluster <br>
      oc project dev <br>
      oc create sa jenkins-user <br>
      oc adm policy add-cluster-role-to-user edit -z jenkins-user <br>
      oc describe sa jenkins-user <br>
      oc describe secret jenkins-user-token-xxxx <br>
- Extend Jenkins pipeline to deploy the stateless nodejs app onto OCP 4 <br>
    oc new-project dev --display-name="Tasks - Dev" <br>
    oc new-project cicd --display-name="CI/CD" <br>
    oc policy add-role-to-group edit system:serviceaccounts:cicd -n dev <br>
    oc new-app -n cicd -f cicd-template.yaml <br>


