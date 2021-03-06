---
title: "&lt;类型实例化&gt;元素 (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# &lt;类型实例化&gt;元素 (.NET Native)
将运行时反射策略应用到一个构造泛型类型。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<TypeInstantiation Name="type_name"  
                   Arguments="type_arguments"  
                   Activate="policy_type"  
                   Browse="policy_type"  
                   Dynamic="policy_type"  
                   Serialize="policy_type"  
                   DataContractSerializer="policy_setting"  
                   DataContractJsonSerializer="policy_setting"  
                   XmlSerializer="policy_setting"  
                   MarshalObject="policy_setting"  
                   MarshalDelegate="policy_setting"  
                   MarshalStructure="policy_setting" />  
  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|特性类型|说明|  
|---------------|--------------------|-----------------|  
|`Name`|常规|必需的特性。 指定类型名称。|  
|`Arguments`|常规|必需的特性。 指定泛型类型参数。 如果存在多个自变量，它们之间用逗号分割。|  
|`Activate`|映像|可选特性。 控制运行时对构造函数的访问，以启用实例激活。|  
|`Browse`|映像|可选特性。 控制对有关程序元素信息的查询，但并不启用任何运行时访问。|  
|`Dynamic`|映像|可选特性。 控制运行时对所有类型成员的访问，包括构造函数、方法、字段、属性和事件，以启用动态编程。|  
|`Serialize`|序列化|可选特性。 控制运行时对构造函数、字段和属性的访问，使类型实例得到序列化和反序列化处理，这是通过库进行的，例如 Newtonsoft JSON 序列化程序。|  
|`DataContractSerializer`|序列化|可选特性。 控制使用的序列化策略<xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>类。|  
|`DataContractJsonSerializer`|序列化|可选特性。 控制使用的 JSON 序列化策略<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName>类。|  
|`XmlSerializer`|序列化|可选特性。 控制使用的 XML 序列化策略<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>类。|  
|`MarshalObject`|Interop|可选特性。 控制封送引用类型到 Windows 运行时和 COM 的策略。|  
|`MarshalDelegate`|Interop|可选特性。 控制将委托类型作为函数指针封送到本机代码的策略。|  
|`MarshalStructure`|Interop|可选特性。 控制封送结构到本机代码的策略。|  
  
## <a name="name-attribute"></a>Name 特性  
  
|值|描述|  
|-----------|-----------------|  
|*类型 _ 名称*|类型名称。 如果此`<TypeInstantiation>`元素是子[ <> \> ](../../../docs/framework/net-native/namespace-element-net-native.md)元素， [ <> \> ](../../../docs/framework/net-native/type-element-net-native.md)元素，或另一个`<TypeInstantiation>`元素， *type_name*可以指定而无需其命名空间类型的名称。 否则为*类型 _ 名称*必须包含完全限定的类型名称。 该类型名称没有经过修饰。 例如，对于<xref:System.Collections.Generic.List%601?displayProperty=fullName>对象，`<TypeInstantiation>`元素可能会出现，如下所示︰<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>自变量特性  
  
|值|描述|  
|-----------|-----------------|  
|*type_argument*|指定泛型类型参数。 如果存在多个参数，它们之间用逗号分割。 每个参数必须包含一个完全限定的类型名称。|  
  
## <a name="all-other-attributes"></a>所有其他特性  
  
|值|说明|  
|-----------|-----------------|  
|*policy_setting*|该设置将应用到这个构造泛型类型的策略类型。 可能值为 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 以及 `Required All`。 有关详细信息，请参阅[运行时指令策略设置](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/event-element-net-native.md)|将反射策略应用到属于这种类型的一个事件。|  
|[<>\>](../../../docs/framework/net-native/field-element-net-native.md)|将反射策略应用到属于这种类型的一个字段。|  
|[<>\>](../../../docs/framework/net-native/impliestype-element-net-native.md)|如果该策略已应用到以包含 `<TypeInstantiation>` 元素为代表的类型，将该策略应用到一个类型。|  
|[<>\>](../../../docs/framework/net-native/method-element-net-native.md)|将反射策略应用到属于这种类型的一个方法。|  
|[<>\>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|将反射策略应用到属于这种类型的一个构造泛型方法。|  
|[<>\>](../../../docs/framework/net-native/property-element-net-native.md)|将反射策略应用到属于这种类型的一个属性。|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|将反射策略应用到一个嵌套类型。|  
|`<TypeInstantiation>`|将反射策略应用到一个嵌套的构造泛型类型。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/application-element-net-native.md)|作为应用程序范围内的类型和元数据可以反应在运行时间的类型成员的容器而服务。|  
|[<>\>](../../../docs/framework/net-native/assembly-element-net-native.md)|将反射策略应用到指定程序集中的所有类型。|  
|[<>\>](../../../docs/framework/net-native/library-element-net-native.md)|定义包含元数据在运行时间可以用于反射的类型和类型成员的程序集。|  
|[<>\>](../../../docs/framework/net-native/namespace-element-net-native.md)|将反射策略应用到命名空间中的所有类型。|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|将反射策略应用到一种类型及其所有成员。|  
|`<TypeInstantiation>`|将反射策略应用到一种构造泛型类型及其所有成员。|  
  
## <a name="remarks"></a>备注  
 反射、序列化和互操作特性都是可选项。 然而，至少一个特性必须存在。  
  
 如果`<TypeInstantiation>`元素是子[ <> \</> \> ](../../../docs/framework/net-native/assembly-element-net-native.md)， [ <> \</> \> ](../../../docs/framework/net-native/namespace-element-net-native.md)，或[ <> \</> \> ](../../../docs/framework/net-native/type-element-net-native.md)，元素，它会替代由父元素定义的策略设置。 如果[ <> \> ](../../../docs/framework/net-native/type-element-net-native.md)元素定义一个相应的泛型类型定义，`<TypeInstantiation>`元素会替代仅为指定的构造泛型类型的实例化的运行时反射策略。  
  
## <a name="example"></a>示例  
 下面的示例使用反射来检索从一个构造泛型类型定义<xref:System.Collections.Generic.Dictionary%602>对象。</TKey, TValue> 它还使用反射来展示有关<xref:System.Type>这些对象表示构造的泛型类型和泛型类型定义。 该变量`b`在示例中是[TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx)控件。  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 编译后[!INCLUDE[net_native](../../../includes/net-native-md.md)]工具链之中，本示例将引发[丢失元数据异常](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)异常调用的行上<xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=fullName>方法。 你可通过将以下 `<TypeInstantiation>` 元素添加到运行时指令文件来消除异常并提供必需的元数据：  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
     <TypeInstantiation Name="System.Collections.Generic.Dictionary"  
                        Arguments="System.String,GenericType.Example"  
                        Dynamic="Required Public" />  
  </Application>  
</Directives>  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [运行时指令 (rd.xml) 配置文件引用](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [运行时指令元素](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [运行时指令策略设置](../../../docs/framework/net-native/runtime-directive-policy-settings.md)