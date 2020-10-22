# AWS Notes
## Image Annotation.
1. CVAT can be deployed in EC2 usng the following [guide](https://github.com/openvinotoolkit/cvat/blob/develop/cvat/apps/documentation/AWS-Deployment-Guide.md)
    There are two ways of deploying the CVAT.
    1. **On Nvidia GPU Machine:** 
    
        Tensorflow annotation feature is dependent on GPU hardware. One of the easy ways to launch CVAT with the tf-annotation app is to use AWS P3 instances, which provides the NVIDIA GPU. Read more about P3 instances here. Overall setup instruction is explained in main readme file, except Installing Nvidia drivers. So we need to download the drivers and install it. For Amazon P3 instances, download the Nvidia Drivers from Nvidia website. For more check Installing the NVIDIA Driver on Linux Instances link.

    2. **On Any other AWS Machine:**
   
        We can follow the same instruction guide mentioned in the installation instructions. The additional step is to add a security group and rule to allow incoming connections.

    3. For any of above, don't forget to add exposed AWS public IP address or hostname to docker-compose.override.yml:
        ```yaml
        version: "2.3"
        services:
        cvat_proxy:
            environment:
            CVAT_HOST: your-instance.amazonaws.com
        ```
