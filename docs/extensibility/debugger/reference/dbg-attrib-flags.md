---
title: "DBG_ATTRIB_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DBG_ATTRIB_FLAGS"
helpviewer_keywords: 
  - "Enumeraciones DBGPROP_ATTRIB_FLAGS"
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# DBG_ATTRIB_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Describe los distintos atributos para [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) o una interfaz de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .  miembro de la estructura de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .  
  
## Sintaxis  
  
```cpp#  
#define DBG_ATTRIB_NONE                 0x0000000000000000,  
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,  
  
// Attributes about the object itself  
  
#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,  
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,  
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,  
  
// Attributes about the value of the object  
  
#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,  
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,  
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,  
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,  
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,  
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,  
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,  
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,  
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,  
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,  
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,  
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,  
  
// Attributes about field access types for the object  
  
#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,  
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,  
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,  
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,  
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,  
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,  
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,  
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,  
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,  
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,  
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,  
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,  
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,  
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,  
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
#define DBG_ATTRIB_DATA                 0x0000010000000000,  
#define DBG_ATTRIB_METHOD               0x0000020000000000,  
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,  
#define DBG_ATTRIB_CLASS                0x0000080000000000,  
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,  
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,  
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,  
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,  
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000  
  
typedef UINT64 DBG_ATTRIB_FLAGS;  
```  
  
```c#  
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,  
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,  
  
// Attributes about the object itself  
  
public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,  
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,  
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,  
  
// Attributes about the value of the object  
  
public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,  
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,  
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,  
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,  
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,  
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,  
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,  
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,  
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,  
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,  
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,  
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,  
  
// Attributes about field access types for the object  
  
public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,  
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,  
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,  
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,  
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,  
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,  
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,  
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,  
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,  
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,  
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,  
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,  
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,  
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,  
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,  
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,  
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,  
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,  
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,  
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,  
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,  
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,  
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000  
```  
  
## Members  
 DBG\_ATTRIB\_NONE  
 Indica que no hay ningún atributo.  
  
 DBG\_ATTRIB\_ALL  
 indica todos los atributos.  
  
 DBG\_ATTRIB\_OBJ\_IS\_EXPANDABLE  
 indica que la referencia o la propiedad tiene elementos secundarios.  
  
 DBG\_ATTRIB\_OBJ\_HAS\_ID  
 Indica que un identificador de este objeto se ha creado.  
  
 DBG\_ATTRIB\_OBJ\_CAN\_HAVE\_ID  
 Indica que un identificador de este objeto puede ser creado.  
  
 DBG\_ATTRIB\_VALUE\_READONLY  
 Indica que el valor es de solo lectura.  
  
 DBG\_ATTRIB\_VALUE\_ERROR  
 indica que el valor es un error.  
  
 DBG\_ATTRIB\_VALUE\_SIDE\_EFFECT  
 indica que la evaluación tenía un efecto secundario.  
  
 DBG\_ATTRIB\_OVERLOADED\_CONTAINER  
 indica que esta propiedad es realmente un contenedor de sobrecargas.  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN  
 Indica que el valor de `DEBUG_PROPERTY_INFO::bstrValue` es booleano.  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN\_TRUE  
 Indica que el valor de `DEBUG_PROPERTY_INFO::bstrValue` es booleano y `TRUE`.  
  
 DBG\_ATTRIB\_VALUE\_INVALID  
 Indica que el valor de `DEBUG_PROPERTY_INFO::bstrValue` no es válido.  
  
 DBG\_ATTRIB\_VALUE\_NAT  
 Indica que el valor de `DEBUG_PROPERTY_INFO::bstrValue` es “*no algo*” \(NAT\).  NAT describe un indicador de registro en los procesadores Intel de 64 bits que indica excepciones especulativas diferidas.  
  
 DBG\_ATTRIB\_VALUE\_AUTOEXPANDED  
 Indica que automáticamente ha expandido el valor en `DEBUG_PROPERTY_INFO::bstrValue` posiblemente.  
  
 DBG\_ATTRIB\_VALUE\_TIMEOUT  
 Indica que una evaluación ha agotado el tiempo de espera.  
  
 DBG\_ATTRIB\_VALUE\_RAW\_STRING  
 Indica que el valor de `DEBUG_PROPERTY_INFO::bstrValue` se puede representar mediante una cadena sin formato.  
  
 DBG\_ATTRIB\_VALUE\_CUSTOM\_VIEWER  
 Indica que esta propiedad tiene al menos un visor personalizado asociado.  
  
 DBG\_ATTRIB\_ACCESS\_NONE  
 Indica un objeto que tiene ni `public`, `private`, ni acceso de tipo de `protected` .  
  
 DBG\_ATTRIB\_ACCESS\_PUBLIC  
 Indica un objeto que tiene acceso público.  
  
 DBG\_ATTRIB\_ACCESS\_PRIVATE  
 Indica un objeto que tiene acceso privado.  
  
 DBG\_ATTRIB\_ACCESS\_PROTECTED  
 indica un objeto que ha protegido el acceso.  
  
 DBG\_ATTRIB\_ACCESS\_FINAL  
 Indica un objeto que tiene acceso final.  
  
 DBG\_ATTRIB\_ACCESS\_ALL  
 Máscara para extraer los atributos de acceso de `DBG_ATTRIB_FLAGS`.  
  
 DBG\_ATTRIB\_STORAGE\_NONE  
 Indica que no hay ningún tipo de almacenamiento especificado.  
  
 DBG\_ATTRIB\_STORAGE\_GLOBAL  
 indica almacenamiento global.  
  
 DBG\_ATTRIB\_STORAGE\_STATIC  
 indica almacenamiento estático.  
  
 DBG\_ATTRIB\_STORAGE\_REGISTER  
 indica almacenamiento en el registro.  
  
 DBG\_ATTRIB\_STORAGE\_ALL  
 máscara para extraer los atributos de almacenamiento de `DBG_ATTRIB_FLAGS`.  
  
 DBG\_ATTRIB\_TYPE\_NONE  
 Indica que no hay ningún modificador de tipo.  
  
 DBG\_ATTRIB\_TYPE\_VIRTUAL  
 indica que el tipo de objeto es virtual.  
  
 DBG\_ATTRIB\_TYPE\_CONSTANT  
 indica que el tipo de objeto es constante.  
  
 DBG\_ATTRIB\_TYPE\_SYNCHRONIZED  
 Indica que sincronizan el tipo de objeto.  
  
 DBG\_ATTRIB\_TYPE\_VOLATILE  
 Indica que el tipo de objeto son volátiles.  
  
 DBG\_ATTRIB\_TYPE\_ALL  
 máscara para extraer los atributos de tipo de `DBG_ATTRIB_FLAGS`.  
  
 DBG\_ATTRIB\_DATA  
 indica que este objeto es un campo de datos.  
  
 DBG\_ATTRIB\_METHOD  
 indica que este objeto es un método.  
  
 DBG\_ATTRIB\_PROPERTY  
 indica que este objeto es una propiedad.  
  
 DBG\_ATTRIB\_CLASS  
 indica que este objeto es una clase.  
  
 DBG\_ATTRIB\_BASECLASS  
 indica que este objeto es una clase base.  
  
 DBG\_ATTRIB\_INTERFACE  
 indica que este objeto es una interfaz.  
  
 DBG\_ATTRIB\_INNERCLASS  
 indica que este objeto es una clase interna.  
  
 DBG\_ATTRIB\_MOSTDERIVED  
 Indica que este objeto es “*forma*”.  El término “*forma*” significa el tipo real del objeto, y no el tipo de la referencia.  
  
 DBG\_ATTRIB\_CHILD\_ALL  
 indica una máscara de `DBG_ATTRIB_DATA` con `DBG_ATTRIB_MOSTDERIVED`.  
  
 DBG\_ATTRIB\_MULTI\_CUSTOM\_VIEWERS  
 Indica que el objeto tiene visores personalizados varias asociado.  
  
## Comentarios  
  
> [!NOTE]
>  Los valores de esta enumeración no son realmente definido en el ensamblado para C\#.  En su lugar, debe copiar definiciones del archivo de código fuente.  
  
 Estos marcadores también se usan para filtrar los elementos secundarios de un objeto, por ejemplo, cuando se pasan como argumento a [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md).  los valores se pueden combinar con `OR`bit a bit.  
  
 El indicador de `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` es una indicación a [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] de obtener la interfaz de [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) de la interfaz de [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) y de llamar a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) para una lista de visores personalizados.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)