# Computer Vision Hacks
## Data Annotation
1. CVAT working in AWS. Use host ip instead of host name `CVAT_HOST` in `docker-compose.override.yml`
    ```yaml
    version: "3.3"
    services:
        cvat_proxy:
            environment:
            CVAT_HOST: <public-ip>
    ```
2. Creating a CVAT task through API. Please follow the link for more info. [github-link](https://github.com/openvinotoolkit/cvat/issues/447)
3. CVAT on remote host with dynamic ip (ip-1: 34.204.197.198, ip-2: 3.238.50.29)