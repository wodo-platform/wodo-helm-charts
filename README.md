
<p align="center">
  <a href="http://wodoplatform.io/" target="blank"><img src="https://github.com/wodo-platform/wodo-docs/images/wodo_logo_large.png" width="320" alt="Wodo Platform" /></a>
</p>


<h2> Wodo Helm Charts Repository</h2>

wodo-docs component includes all type of documentations about Wodo Platform

<div align="center">
  <h4>
    <a href="#">
      Website
    </a>
    <span> | </span>
    <a href="#">
      Product Docs
    </a>
    <span> | </span>
    <a href="#">
      Architecture Docs
    </a>
    <span> | </span>
    <!-- <a href="#"> -->
    <!--   CLI -->
    <!-- </a> -->
    <!-- <span> | </span> -->
    <a href="#/CONTRIBUTING.md">
      Contributing
    </a>
    <span> | </span>
    <a href="#">
      Reddit
    </a>
    <span> | </span>
    <a href="#">
      Twitter
    </a>
  </h4>
</div>


<h3> Table of Contents </h3> 


- [About](#about)
- [Add Helm Charts for Repositories](#add-helm-charts-for-repositories)


# About

Released helm charts for each wodo repository are stored in git helm registery. There is a limitation regarding how github enables helm registery on a repository. In order to have central helm registery , all helm charts are kept and released in this single repository. We can change this design once we have another helm registery.

# Add Helm Charts for Repositories

Please follow the steps below in order to add helm charts for a specific repository/module. 

- Create default helm deployment charts by running the command:  

    ```shall
    helm create {your_module_name}
    ```

- Go into the generete project folder and add the following dependency to end of Chart.yaml file. Please change the version respectively. This dependency enables inheritance for underneath helm chart definitions
- 
    ```shall
    dependencies:
    - name: node-helm-chart
      version: 1.0.13
      repository: https://wodo-platform.github.io/wodo-helm-charts/
    ```
- Copy values.yaml from wodo-payment-api folder and fix project name and other settings. 

Once you release wodo-helm-chart on github, the added/updated helm charts will be available in the github helm registery that is also hosted by github

Now we will explain how to deploy modules manually to your minikube cluster

- You need to build your project and docker image and add the composed docker image to your lcoal repo..It is a standard procedure if you read this document