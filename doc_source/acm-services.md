# Services Integrated with AWS Certificate Manager<a name="acm-services"></a>

AWS Certificate Manager supports a growing number of AWS services\. You cannot install your ACM certificate or your private ACM PCA certificate directly on your AWS based website or application\. You must use one of the following services\. 

**Elastic Load Balancing**  
 Elastic Load Balancing automatically distributes your incoming application traffic across multiple Amazon EC2 instances\. It detects unhealthy instances and reroutes traffic to healthy instances until the unhealthy instances have been restored\. Elastic Load Balancing automatically scales its request handling capacity in response to incoming traffic\. For more information about load balancing, see the [Elastic Load Balancing User Guide](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/)\.  
In general, to serve secure content over SSL/TLS, load balancers require that SSL/TLS certificates be installed on either the load balancer or the backend Amazon EC2 instance\. ACM is integrated with Elastic Load Balancing to deploy ACM certificates on the load balancer\. For more information, see [ Create an Application Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/create-application-load-balancer.html)\.

**Amazon CloudFront**  
Amazon CloudFront is a web service that speeds up distribution of your dynamic and static web content to end users by delivering your content from a worldwide network of edge locations\. When an end user requests content that you're serving through CloudFront, the user is routed to the edge location that provides the lowest latency\. This ensures that content is delivered with the best possible performance\. If the content is currently at that edge location, CloudFront delivers it immediately\. If the content is not currently at that edge location, CloudFront retrieves it from the Amazon S3 bucket or web server that you have identified as the definitive content source\. For more information about CloudFront, see the [Amazon CloudFront Developer Guide](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/)\.  
To serve secure content over SSL/TLS, CloudFront requires that SSL/TLS certificates be installed on either the CloudFront distribution or on the backend content source\. ACM is integrated with CloudFront to deploy ACM certificates on the CloudFront distribution\. For more information, see [ Getting an SSL/TLS Certificate](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cnames-and-https-procedures.html#cnames-and-https-getting-certificates)\.  
To use an ACM certificate with CloudFront, you must request or import the certificate in the US East \(N\. Virginia\) region\.

**AWS Elastic Beanstalk**  
Elastic Beanstalk helps you deploy and manage applications in the AWS Cloud without worrying about the infrastructure that runs those applications\. AWS Elastic Beanstalk reduces management complexity\. You simply upload your application and Elastic Beanstalk automatically handles the details of capacity provisioning, load balancing, scaling, and health monitoring\. Elastic Beanstalk uses the Elastic Load Balancing service to create a load balancer\. For more information about Elastic Beanstalk, see the [AWS Elastic Beanstalk Developer Guide](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/)\.  
To choose a certificate, you must configure the load balancer for your application in the Elastic Beanstalk console\. For more information, see [ Configuring Your Elastic Beanstalk Environment's Load Balancer to Terminate HTTPS](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/configuring-https-elb.html)\. 

**Amazon API Gateway**  
 With the proliferation of mobile devices and growth of the Internet of Things \(IoT\), it has become increasingly common to create APIs that can be used to access data and interact with back\-end systems on AWS\. You can use API Gateway to publish, maintain, monitor, and secure your APIs\. After you deploy your API to API Gateway, you can [set up a custom domain name](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-custom-domains.html) to simplify access to it\. To set up a custom domain name, you must provide an SSL/TLS certificate\. You can use ACM to generate or import the certificate\. 

**AWS CloudFormation**  
AWS CloudFormation helps you model and set up your Amazon Web Services resources\. You create a template that describes the AWS resources that you want to use, such as Elastic Load Balancing or API Gateway\. Then AWS CloudFormation takes care of provisioning and configuring those resources for you\. You don't need to individually create and configure AWS resources and figure out what's dependent on what; AWS CloudFormation handles all of that\. ACM certificates are included as a template resource, which means that AWS CloudFormation can request ACM certificates that you can use with AWS services to enable secure connections\. For more information, see [AWS::CertificateManager::Certificate](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-certificatemanager-certificate.html)\. In addition, ACM certificates are included with many of the AWS resources that you can set up with AWS CloudFormation\.   
 If you create an ACM certificate with AWS CloudFormation, the AWS CloudFormation stack remains in the **CREATE\_IN\_PROGRESS** state\. Any further stack operations are delayed until you act upon the instructions in the certificate validation email\. For more information, see [ Resource Failed to Stabilize During a Create, Update, or Delete Stack Operation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/troubleshooting.html#troubleshooting-resource-did-not-stabilize)\. 