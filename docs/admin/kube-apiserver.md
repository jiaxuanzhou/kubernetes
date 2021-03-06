<!-- BEGIN MUNGE: UNVERSIONED_WARNING -->

<!-- BEGIN STRIP_FOR_RELEASE -->

<img src="http://kubernetes.io/img/warning.png" alt="WARNING"
     width="25" height="25">
<img src="http://kubernetes.io/img/warning.png" alt="WARNING"
     width="25" height="25">
<img src="http://kubernetes.io/img/warning.png" alt="WARNING"
     width="25" height="25">
<img src="http://kubernetes.io/img/warning.png" alt="WARNING"
     width="25" height="25">
<img src="http://kubernetes.io/img/warning.png" alt="WARNING"
     width="25" height="25">

<h2>PLEASE NOTE: This document applies to the HEAD of the source tree</h2>

If you are using a released version of Kubernetes, you should
refer to the docs that go with that version.

<!-- TAG RELEASE_LINK, added by the munger automatically -->
<strong>
The latest release of this document can be found
[here](http://releases.k8s.io/release-1.1/docs/admin/kube-apiserver.md).

Documentation for other releases can be found at
[releases.k8s.io](http://releases.k8s.io).
</strong>
--

<!-- END STRIP_FOR_RELEASE -->

<!-- END MUNGE: UNVERSIONED_WARNING -->

## kube-apiserver



### Synopsis


The Kubernetes API server validates and configures data
for the api objects which include pods, services, replicationcontrollers, and
others. The API Server services REST operations and provides the frontend to the
cluster's shared state through which all other components interact.

```
kube-apiserver
```

### Options

```
      --admission-control="AlwaysAdmit": Ordered list of plug-ins to do admission control of resources into cluster. Comma-delimited list of: AlwaysAdmit, AlwaysDeny, AlwaysPullImages, DenyEscalatingExec, DenyExecOnPrivileged, InitialResources, LimitRanger, NamespaceAutoProvision, NamespaceExists, NamespaceLifecycle, PersistentVolumeLabel, ResourceQuota, SecurityContextDeny, ServiceAccount
      --admission-control-config-file="": File with admission control configuration.
      --advertise-address=<nil>: The IP address on which to advertise the apiserver to members of the cluster. This address must be reachable by the rest of the cluster. If blank, the --bind-address will be used. If --bind-address is unspecified, the host's default interface will be used.
      --allow-privileged[=false]: If true, allow privileged containers.
      --apiserver-count=1: The number of apiservers running in the cluster
      --authorization-mode="AlwaysAllow": Ordered list of plug-ins to do authorization on secure port. Comma-delimited list of: AlwaysAllow,AlwaysDeny,ABAC,Webhook
      --authorization-policy-file="": File with authorization policy in csv format, used with --authorization-mode=ABAC, on the secure port.
      --authorization-webhook-config-file="": File with webhook configuration in kubeconfig format, used with --authorization-mode=Webhook. The API server will query the remote service to determine access on the API server's secure port.
      --basic-auth-file="": If set, the file that will be used to admit requests to the secure port of the API server via http basic authentication.
      --bind-address=0.0.0.0: The IP address on which to listen for the --secure-port port. The associated interface(s) must be reachable by the rest of the cluster, and by CLI/web clients. If blank, all interfaces will be used (0.0.0.0).
      --cert-dir="/var/run/kubernetes": The directory where the TLS certs are located (by default /var/run/kubernetes). If --tls-cert-file and --tls-private-key-file are provided, this flag will be ignored.
      --client-ca-file="": If set, any request presenting a client certificate signed by one of the authorities in the client-ca-file is authenticated with an identity corresponding to the CommonName of the client certificate.
      --cloud-config="": The path to the cloud provider configuration file.  Empty string for no configuration file.
      --cloud-provider="": The provider for cloud services.  Empty string for no provider.
      --cors-allowed-origins=[]: List of allowed origins for CORS, comma separated.  An allowed origin can be a regular expression to support subdomain matching.  If this list is empty CORS will not be enabled.
      --delete-collection-workers=1: Number of workers spawned for DeleteCollection call. These are used to speed up namespace cleanup.
      --etcd-prefix="/registry": The prefix for all resource paths in etcd.
      --etcd-quorum-read[=false]: If true, enable quorum read
      --etcd-servers=[]: List of etcd servers to watch (http://ip:port), comma separated. Mutually exclusive with -etcd-config
      --etcd-servers-overrides=[]: Per-resource etcd servers overrides, comma separated. The individual override format: group/resource#servers, where servers are http://ip:port, semicolon separated.
      --event-ttl=1h0m0s: Amount of time to retain events. Default 1 hour.
      --experimental-keystone-url="": If passed, activates the keystone authentication plugin
      --external-hostname="": The hostname to use when generating externalized URLs for this master (e.g. Swagger API Docs.)
      --google-json-key="": The Google Cloud Platform Service Account JSON Key to use for authentication.
      --insecure-bind-address=127.0.0.1: The IP address on which to serve the --insecure-port (set to 0.0.0.0 for all interfaces). Defaults to localhost.
      --insecure-port=8080: The port on which to serve unsecured, unauthenticated access. Default 8080. It is assumed that firewall rules are set up such that this port is not reachable from outside of the cluster and that port 443 on the cluster's public address is proxied to this port. This is performed by nginx in the default setup.
      --kubelet-certificate-authority="": Path to a cert. file for the certificate authority.
      --kubelet-client-certificate="": Path to a client cert file for TLS.
      --kubelet-client-key="": Path to a client key file for TLS.
      --kubelet-https[=true]: Use https for kubelet connections
      --kubelet-timeout=5s: Timeout for kubelet operations
      --kubernetes-service-node-port=0: If non-zero, the Kubernetes master service (which apiserver creates/maintains) will be of type NodePort, using this as the value of the port. If zero, the Kubernetes master service will be of type ClusterIP.
      --log-flush-frequency=5s: Maximum number of seconds between log flushes
      --long-running-request-regexp="(/|^)((watch|proxy)(/|$)|(logs?|portforward|exec|attach)/?$)": A regular expression matching long running requests which should be excluded from maximum inflight request handling.
      --master-service-namespace="default": The namespace from which the kubernetes master services should be injected into pods
      --max-connection-bytes-per-sec=0: If non-zero, throttle each user connection to this number of bytes/sec.  Currently only applies to long-running requests
      --max-requests-inflight=400: The maximum number of requests in flight at a given time.  When the server exceeds this, it rejects requests.  Zero for no limit.
      --min-request-timeout=1800: An optional field indicating the minimum number of seconds a handler must keep a request open before timing it out. Currently only honored by the watch request handler, which picks a randomized value above this number as the connection timeout, to spread out load.
      --oidc-ca-file="": If set, the OpenID server's certificate will be verified by one of the authorities in the oidc-ca-file, otherwise the host's root CA set will be used
      --oidc-client-id="": The client ID for the OpenID Connect client, must be set if oidc-issuer-url is set
      --oidc-groups-claim="": If provided, the name of a custom OpenID Connect claim for specifying user groups. The claim value is expected to be an array of strings. This flag is experimental, please see the authentication documentation for further details.
      --oidc-issuer-url="": The URL of the OpenID issuer, only HTTPS scheme will be accepted. If set, it will be used to verify the OIDC JSON Web Token (JWT)
      --oidc-username-claim="sub": The OpenID claim to use as the user name. Note that claims other than the default ('sub') is not guaranteed to be unique and immutable. This flag is experimental, please see the authentication documentation for further details.
      --profiling[=true]: Enable profiling via web interface host:port/debug/pprof/
      --repair-malformed-updates[=true]: If true, server will do its best to fix the update request to pass the validation, e.g., setting empty UID in update request to its existing value. This flag can be turned off after we fix all the clients that send malformed updates.
      --runtime-config=: A set of key=value pairs that describe runtime configuration that may be passed to apiserver. apis/<groupVersion> key can be used to turn on/off specific api versions. apis/<groupVersion>/<resource> can be used to turn on/off specific resources. api/all and api/legacy are special keys to control all and legacy api versions respectively.
      --secure-port=6443: The port on which to serve HTTPS with authentication and authorization. If 0, don't serve HTTPS at all.
      --service-account-key-file="": File containing PEM-encoded x509 RSA private or public key, used to verify ServiceAccount tokens. If unspecified, --tls-private-key-file is used.
      --service-account-lookup[=false]: If true, validate ServiceAccount tokens exist in etcd as part of authentication.
      --service-cluster-ip-range=<nil>: A CIDR notation IP range from which to assign service cluster IPs. This must not overlap with any IP ranges assigned to nodes for pods.
      --service-node-port-range=: A port range to reserve for services with NodePort visibility.  Example: '30000-32767'.  Inclusive at both ends of the range.
      --ssh-keyfile="": If non-empty, use secure SSH proxy to the nodes, using this user keyfile
      --ssh-user="": If non-empty, use secure SSH proxy to the nodes, using this user name
      --storage-versions="authorization.k8s.io/v1beta1,autoscaling/v1,batch/v1,componentconfig/v1alpha1,extensions/v1beta1,metrics/v1alpha1,v1": The per-group version to store resources in. Specified in the format "group1/version1,group2/version2,...". In the case where objects are moved from one group to the other, you may specify the format "group1=group2/v1beta1,group3/v1beta1,...". You only need to pass the groups you wish to change from the defaults. It defaults to a list of preferred versions of all registered groups, which is derived from the KUBE_API_VERSIONS environment variable.
      --tls-cert-file="": File containing x509 Certificate for HTTPS.  (CA cert, if any, concatenated after server cert). If HTTPS serving is enabled, and --tls-cert-file and --tls-private-key-file are not provided, a self-signed certificate and key are generated for the public address and saved to /var/run/kubernetes.
      --tls-private-key-file="": File containing x509 private key matching --tls-cert-file.
      --token-auth-file="": If set, the file that will be used to secure the secure port of the API server via token authentication.
      --watch-cache[=true]: Enable watch caching in the apiserver
      --watch-cache-sizes=[]: List of watch cache sizes for every resource (pods, nodes, etc.), comma separated. The individual override format: resource#size, where size is a number. It takes effect when watch-cache is enabled.
```

###### Auto generated by spf13/cobra on 24-Feb-2016


<!-- BEGIN MUNGE: GENERATED_ANALYTICS -->
[![Analytics](https://kubernetes-site.appspot.com/UA-36037335-10/GitHub/docs/admin/kube-apiserver.md?pixel)]()
<!-- END MUNGE: GENERATED_ANALYTICS -->
