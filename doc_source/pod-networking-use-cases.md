# Choosing Pod networking use cases<a name="pod-networking-use-cases"></a>

The Amazon VPC CNI plugin for Kubernetes provides networking for Pods\. The following table helps you understand which networking use cases you can use together and the capabilities and Amazon VPC CNI plugin for Kubernetes settings that you can use with different Amazon EKS node types\. All information in the table applies to Linux `IPv4` nodes only\.

[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/eks/latest/userguide/pod-networking-use-cases.html)

**Note**  
You can't use `IPv6` with custom networking\.
`IPv6` addresses are not translated, so SNAT doesn't apply\.
You can use Calico network policy with `IPv6`\.
Traffic flow to and from Pods with associated security groups are not subjected to Calico network policy enforcement and are limited to Amazon VPC security group enforcement only\. 
IP prefixes and IP addresses are associated with standard Amazon EC2 elastic network interfaces\. Pods requiring specific security groups are assigned the primary IP address of a branch network interface\. You can mix Pods getting IP addresses, or IP addresses from IP prefixes with Pods getting branch network interfaces on the same node\.

**Windows nodes**  
Each node only supports one network interface\. You can use secondary `IPv4` addresses and `IPv4` prefixes\. By default, the number of available `IPv4` addresses on the node is equal to the number of secondary `IPv4` addresses that you can assign to each elastic network interface, minus one\. However, you can increase the available `IPv4` addresses and Pod density on the node by enabling IP prefixes\. For more information, see [Increase the amount of available IP addresses for your Amazon EC2 nodes](cni-increase-ip-addresses.md)\.

Calico network policies are supported on Windows\. For more information, see [Open Source Calico for Windows Containers on Amazon EKS](https://aws.amazon.com/blogs/containers/open-source-calico-for-windows-containers-on-amazon-eks/)\. You can't use [security groups for Pods](security-groups-for-pods.md) or [custom networking](cni-custom-network.md) on Windows\.