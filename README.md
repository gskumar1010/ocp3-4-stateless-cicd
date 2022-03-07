# ocp3-4-stateless-cicd



## Steps
- Authorize Jenkins to deploy onto OCP 4 cluster <br>
      oc project dev <br>
      oc create sa jenkins-user <br>
      oc adm policy add-cluster-role-to-user edit -z jenkins-user <br>
      oc describe sa jenkins-user <br>
      oc describe secret jenkins-user-token-xxxx <br>

Add that token in the credentials section in Jenkins OpenShift Client plugin
![image](https://user-images.githubusercontent.com/19476054/156964951-3835dc71-df17-49a3-8787-0b0f936a4094.png)
![image](https://user-images.githubusercontent.com/19476054/156965011-2b213fe8-4d4d-4ea6-a358-5beabbdb1b36.png)




      
- Extend Jenkins pipeline to deploy the stateless nodejs app onto OCP 4 <br>
    oc new-project dev --display-name="Tasks - Dev" <br>
    oc new-project cicd --display-name="CI/CD" <br>
    oc policy add-role-to-group edit system:serviceaccounts:cicd -n dev <br>
    oc new-app -n cicd -f cicd-template.yaml <br>



