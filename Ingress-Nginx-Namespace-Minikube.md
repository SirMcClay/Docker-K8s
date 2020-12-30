Ingress-Nginx Namespace and Service for Minikube
In the upcoming lecture, we will be adding the ingress-nginx Servicename and Namespace to our axios request. For Minikube users, a few extra steps will be required in order to get ticketing.dev to load the Landing page in your browser.

1. Install add-on

Make sure the add-on has been installed per the docs:

https://kubernetes.github.io/ingress-nginx/deploy/#minikube

2. Find Minikube's IP address

Run minikube ip and add this IP address to your /etc/hosts file instead of 127.0.0.1 (your IP will be different).

Instead of this:

127.0.0.1 ticketing.dev

write this:

172.17.0.3 ticketing.dev

3. Update Servicename and Namespace

The Servicename will be ingress-nginx-controller (which is the same as newer versions ingress-nginx installed by Docker Desktop)

With the minikube add-on, the namespace will be kube-system, per the docs noted here:

https://kubernetes.github.io/ingress-nginx/deploy/#verify-installation

The full URL in your axios request should be:

'http://ingress-nginx-controller.kube-system.svc.cluster.local/api/users/currentuser',

4. Expose the Deployment

kubectl expose deployment ingress-nginx-controller --target-port=80 --type=NodePort -n kube-system

Run kubectl get services -n kube-system to verify. It should look something like this:

ingress-nginx-controller NodePort 10.100.74.124 <none> 80:31562/TCP,443:31233/TCP,8443:30972/TCP 12m

If you need to remove the service you can run this:

kubectl delete service ingress-nginx-controller -n kube-system

5. Visit Application in Browser

Open a new private browsing window (to avoid caching issues) and visit https://ticketing.dev in your browser (it may take a bit to load).

Note - Some students using Linux indicated that they were unable to use the default docker driver and needed to use the virtualbox driver instead. To change the driver you are using, run:

minikube delete

and then:

minikube start --driver=virtualbox

Remember, anytime you delete the cluster you will need to reinstall the ingress add-on and re-apply any secrets.

When using macOS the drivers that should work best are hyper kit or virtualbox (docker driver will not work with ingress on this host).

When using Windows the drivers that should work best are hyperv or virtualbox (docker driver will not work with ingress on this host).

When using Linux (as the host OS, not as a backend for Windows WSL2) the drivers that should work best are docker or virtualbox.

For a list of drivers and info please see the docs:

https://minikube.sigs.k8s.io/docs/drivers/
