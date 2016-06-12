# JsonToObjCClassFile
20160612 releasenote
本次更新主要调整内容：

1-添加了LE_DataModel数据模型基类，自动生成的数据模型类都会基于次基类。

2-LE_DataModel提供了2个接口，分别用于生成单个数据模型（Dic-> obj）和批量数据模型的生成（Array->objs）。
接口如下：

-(id) initWithDataSource:(NSDictionary *) data;

用于单个数据模型的生成，非静态方法。

+(NSArray *) initWithDataSources:(NSArray *) dataArray ClassName:(NSString *) className;

批量数据模型生成采用静态方法。

3-数据模型类前缀“DataModel_”改为“DM_”。

4-不再支持swift（本人尚未学习swift语言）。

5-逻辑优化


JsonToObjCClassFile是一款MAC中使用的类似于JsonToCode的开发工具，可以一键根据Json数据生成一个或多个数据模型于一体的.h和.m类文件到指定目录（MacOS>用户>xxx>DataModels）中，生成后的类文件 拖到xcode即可使用，无需手动创建。类文件全部以“DataModel_”作为前缀，可自定义类名后缀，并且多层json数据自动追加字段名称作为后缀来创建类。同时工具提供了Json数据格式化展示面板，以树形结构展开json数据，方便鼠标滚动查看具体内容。
测试案例：


[{\"id\":14,\"images\":[{\"id\":42,\"imagename\":\"moment_2_1457332231368\",\"timestamp\":1457332149},{\"id\":44,\"imagename\":\"moment_2_1457332231355\",\"timestamp\":1457332145}],\"messages\":[{\"id\":42,\"message\":\"iOS\\u56de\\u590d\\u65b0\\u8bc4\\u8bba\\u7684\\u56de\\u590d\",\"details\":[{\"id\":42,\"content\":\"content\"},{\"id\":42,\"content\":\"content\"}]},{\"id\":42,\"message\":\"\\u56de\\u590d\\u65b0\\u8bc4\\u8bba\",\"details\":[{\"id\":42,\"content\":\"content\"},{\"id\":42,\"content\":\"content\"}]}]}]


![image](https://github.com/LarryEmerson/JsonToObjCClassFile/blob/master/JsonToObjCClassFile/JsonToObjCClassFile.png)

JsonToObjCClassFile是原作者吴海超“WHC_DataModelFactory”的扩展版，
“WHC_DataModelFactory”的github地址：https://github.com/netyouli/WHC_DataModelFactory

生成的类文件请配合WHC_DataModel库使用。

使用方法：

DM_Test *test=[[DM_Test alloc] initWithDataSource:[data JSONValue]];
NSArray *array=[LE_DataModel initWithDataSources:[data JSONValue] ClassName:@"DM_Test"];


具体的“WHC_DataModel”内容，请移步https://github.com/netyouli/WHC_DataModel


JSON，ObjC，Objective-C，DataModel，数据模型，XML，IOS
