# Why only 10 entries return when querying information by using APIs and SDK {#EcsApiSeveralPageResults .reference}

For some APIs request, where returns a large amount of data, the returned data is usually displayed in pages for readability. Take the DescribeImages as an example, if 39 entries are returned, the result is displayed on four pages by default, with 10 entries on each page. Thus, the returned data looks incomplete. To display more data, you can add the PageSize and PageNumber parameters in the following table.

|Parameter|Type|Required|Description|
|:--------|:---|:-------|:----------|
|PageNumber|Integer|No| Page number of the resource status list. Initial value: 1 Default value: 1|
|PageSize|Integer|No|Number of entries on each page, configured during pagination query. Maximum value: 100 Default value: 10|

For example, when you query the available official public mirrors in the region of Singapore by DescribeImages, if 39 entries of data is returned, the result in TotalCount is split into four pages by default. You can add the parameter PageSize in your request, and set it to a value greater than 39. If Java SDK is used, PageSize  can be set to a value greater than 39 by the setPageSize method in the Request object. And then the data about 39 mirrors is returned once.

## Configuration demonstration of Java SDK {#section_kmc_crg_ydb_2 .section}

By default, the value of PageSize is 10. If the value of PageSize is not set to 10, null is returned by getPageSize, The API server sets PageSize to 10 by default.

See the following code snippet:

```
DescribeImagesRequest describe = **new** DescribeImagesRequest();
        //describe.setPageSize(50);//By default value of PageSize is 10.
        describe.setRegionId("cn-hangzhou");
        describe.setImageOwnerAlias("system");
        System.out.println("PageSize of the current request:"+describe.getPageSize());
        DescribeImagesResponse response
                = client.getAcsResponse(describe);

        System.out.println("Total number of images:"+response.getTotalCount());
        System.out.println("Number of images in the returned response="+response.getImages().size());

```

![](images/4033_en-US.jpg)

使用 setPageSize 将 PageSize Set PageSize to 50 by using setPageSize\(\). Then, all images are returned at a time. 

See the following code snippet:

```
DescribeImagesRequest describe = **new** DescribeImagesRequest();
        describe.setPageSize(50);//Here in the Request, the value of PageSize is set to 50 by the setPageSize() method.
        describe.setRegionId("cn-hangzhou");
        describe.setImageOwnerAlias("system");
        System.out.println("PageSize of the current request:"+describe.getPageSize());
        **try** {
            DescribeImagesResponse response
                = client.getAcsResponse(describe);

            System.out.println("Total number of images:"+response.getTotalCount());
            System.out.println("Number of images in the returned response="+response.getImages().size());

```

![](images/4032_en-US.jpg)

**Note:** The maximum value of PageSize is 100. If the query result includes more than 100 entries of data, the data on the last few pages must be obtained by  PageNumber, namely, multiple requests are submitted to obtain all the returned data, with PageNumber setting to 1, 2, 3…respectively. You can also specify the value of PageNumber in your request by `setPageNumber()`.

