#kubectl rollout history deployment.v1.apps/<deployment>
#kubectl rollout history deployment.v1.apps/<deployment> --revision <revision number>
#kubectl rollout undo deployment.v1.apps/<deployment> --to-revision=1
#Rollingupdatestrategy  by default its 25%s