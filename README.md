# ITI-DevOps-Final-Project-Webapp

# Deploy Webapp on kubernetes eks cluster using CI/CD Jenkins pipeline

## Tools
- Terraform
- Amazon Web Services (AWS)
- Jenkins

## Infrastructure Repo
https://github.com/o-muhammad97/ITI-DevOps-Final-Project-infra.git

## Jenkins run successfuly on the browser

![Screenshot from 2023-02-17 22-14-14](https://user-images.githubusercontent.com/50025855/219797198-b4a1530a-b458-4a87-ae56-78c6e2466476.png)


## Get Jenkins Password to login 
```bash
kubectl -n jenkins exec -it pod/jenkins-6bc568ff97-llmn9 cat /var/jenkins_home/secrets/initialAdminPassword
```
![Screenshot from 2023-02-17 22-14-49](https://user-images.githubusercontent.com/50025855/219797223-e86e65d0-bb0d-42ac-b879-1b4b8c398381.png)


## Creating CI/CD Pipeline with Webhook to GitHub repo

![Screenshot from 2023-02-17 23-32-50](https://user-images.githubusercontent.com/50025855/219797966-a971f5df-2792-4973-bff5-d839ba0083fd.png)
![Screenshot from 2023-02-17 22-12-56](https://user-images.githubusercontent.com/50025855/219797996-f7f6eec7-9029-47dd-8d06-c269ef562296.png)

![Screenshot from 2023-02-17 22-08-58](https://user-images.githubusercontent.com/50025855/219798151-21388bef-262e-4812-bb73-ac3447df3784.png)

![Screenshot from 2023-02-17 22-09-50](https://user-images.githubusercontent.com/50025855/219798174-b99e5bd4-9543-43ae-8698-aed7fce5aead.png)

![Screenshot from 2023-02-17 22-10-32](https://user-images.githubusercontent.com/50025855/219798216-282cac85-c1cb-4862-99af-75ac1e32e049.png)

## kubectl -n app get all


## Jenkins exposed externaly
http://a571e4e3315a647778f710fdc1607add-1530429796.us-east-1.elb.amazonaws.com




## Webapp exposed externaly
http://af5482a4cd6f448ed9c403f1292ecf00-1916157188.us-east-1.elb.amazonaws.com




## Lessons learned

I learned how to configure kubernetes cluster on AWS, acquired experiences on AWS platform and learned how to use all the tools together for development life cycle 
