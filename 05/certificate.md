#### step1:
Pre-req
openssl and nano needs to be installed

#### create priv key and CSR:
openssl genrsa -out test.key 2048
openssl req -new -key test.key -out test.csr "/CN=abc/O=def"

### encode CSR cuz k8 only accepts base64 encoded crt
cat test.csr | base64 

### generate CertificateSigningRequest object for kube api server

apiVersion: certificates.k8s.io/v1beta1
kind: CertificateSigningRequest
metadata:
  name: test-csr
spec:
  groups:
  - system:authenticated
  request: ADD-YOUR-CSR-HERE
  usages:
  - digital signature
  - key encipherment
  - client auth

### kubectl apply -f signingrequest.yaml
### Verify with  kubectl get csr

### aprrove csr
kubectl certificate approve test-csr


### download cert from csr for configuring kube

kubectl get csr test-csr -o json 

### decode csr fron base64

echo "CERTIFICATE" > base64 -d

### create new context in ~/.kube/config file

kubectl config set-credentials test - client-certificate=test.crt --client-key=test.key

### set new context

Kubectl config set-context test-context --cluster "cluster-name" --user=test

### verify configuration

kubectl --context=test-context get pods