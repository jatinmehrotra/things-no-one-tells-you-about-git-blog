> In any SDLC task or Devops task, working with **version control is inevitable**.
>
> People often focus on DSA, database, networking and various other fundamentals which are important but ***learning version control tool like git is a skill which is as important as any other fundamentals***.
>
> This blog talks about the `everyday usecases with git` which every developer or devops engineer will certainly face during their projects and **the purpose of this blog is to help you learn from my experience** which I faced when  I started working. ( I learned it the hard way, hope it helps in your learning journey)
>
>

## Prequisites

- Understanding of why do we need a version control?
- Understanding of [git](https://git-scm.com) ( how to play around and commands ).


# UseCases

## When another developer push their changes to same branch on remote

- **Scenario**: You and your teammate is working on the same branch, however he/she pushed their commit changes to remote.
- You are still working on your local, and when you try to push your changes to remote; you simple can't!



- **Views**:- It's like a filter. Queries go through the filter -> Aggregator -> Local Index. In the case of the Local index
filter -> Local Index

- * Views help in controlling the visibility of resources in my account by creating views that define what resource information is available for search and discovery. These controls are not based only on resources but also on the information that resources bring.*
- **Aggregator Index**: query can search across all indexed Regions.
- **Local index**: then the query has access only to the resources in that Region.

## Let's find some resources!!!

- **Turn it on**:- you must turn on Resource Explorer and let it build an index of your resources.
- There are two options to turn on `Quick set-up` and `Advanced set-up`

![2 options turn on](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2022/11/Screenshot-2022-11-09-at-1.34.00-PM.png)

- **Quick set-up**: This option creates local indexes in all Regions and an aggregator index in the selected Region. A default view with a filter that includes all supported resources in the account is also created in the same Region as the aggregator index. It provides visibility to all resources. Aggregator index turn on searching across all regions in this account.

![quick view](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2022/11/Screenshot-2022-11-09-at-1.35.06-PM.png)
- **Advanced setup**: Perfect for governance requirements where we have more granular controls like creating an index in a selected region, where you can choose to create a default view or your custom view. With the Advanced setup option, I have access to more granular controls that are useful when there are specific governance requirements. For example, I can select in which Regions to create indexes. I can choose not to replicate resource information to any other Region so that resources from each AWS Region are searchable only from within the same Region. I can also control what information is available in the default view or avoid the creation of the default view.

![advanced setup](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2022/11/Screenshot-2022-11-09-at-1.36.40-PM.png)

![advanced setup 2](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2022/11/Screenshot-2022-11-09-at-1.36.51-PM.png)

- **Note:** It can take up to 36 hours to index all the resources in the account.

![36 hours](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2022/11/Screenshot-2022-11-09-at-1.37.37-PM.png)

- After turning it on, **proceed to resource search**, here I have the option to choose my views ( currently default view)

![process](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2022/11/Screenshot-2022-11-09-at-1.39.09-PM.png)
- In the query, we can add keywords, filters, attributes and operators and wildcards. Here in this example, I will find resources related to the identifier **"jatin"** to search the resources which I use for my reference.

![empty usage](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2022/11/Screenshot-2022-11-09-at-1.41.01-PM.png)

![basic usage](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2022/11/Screenshot-2022-11-09-at-1.44.54-PM.png)

- I can also limit the results to specific services using the **:** operator.

![use of :](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2022/11/Screenshot-2022-11-09-at-1.47.30-PM.png)

!(use of : 2](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2022/11/Screenshot-2022-11-09-at-1.46.40-PM.png)

- I can also search resources using Tags for example searching resource where Name is key and whose value is module 1 **(tag:Name=module1)**

![tags use](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2022/11/Screenshot-2022-11-09-at-1.51.04-PM.png)

- I can create a custom view to limit access to resource discovery by using custom views and then attach an identity-based policy to the users and roles who are only required to use this view.

![custom view](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2022/11/Screenshot-2022-11-09-at-1.54.49-PM.png)

## The birth of Unified Search in the Management Console

- **If I have the default view in the same Region that contains the aggregator index **then I can also use a capability called **Unified view ** which allows me to search through AWS resources.
- Here in the console I can search for resources using `/Resources` "attribute to search" for example `/Resources Jatin`



### Additional Information

- There are other services too which help to manage AWS resources like AWS RAM, AWS Resource groups and TAG editor.
- To build and understand how  search query works in a better way [docs are the most helpful piece of information.](https://docs.aws.amazon.com/resource-explorer/latest/userguide/using-search-query-syntax.html)
- [Quotas](https://docs.aws.amazon.com/resource-explorer/latest/userguide/quotas.html) is something we should be aware of as it talks about the number of views in the region and the number of search operations per second


## Use cases

- **Save more**: You can search and understand your application resources in a better way.
- **Better Response to Alerts**: Address alerts by finding and navigating to relevant resources directly from the unified search bar in the AWS Management Console.
- **Better Compliance**: Quickly identify untagged resources across AWS regions using named operators like "Jatin" or "example-resource"

### From DevOps Perspective

- AWS Resource Explorer is integrated with AWS CLI, AWS SDKs, and Query API which allows us to build automation for searching our service.

Till then, **Happy Learning!**