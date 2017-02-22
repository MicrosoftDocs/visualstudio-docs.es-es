---
title: "Iconos de la Vista de clases y del Examinador de objetos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "iconos, en el Examinador de objetos"
  - "iconos de señal"
  - "Herramienta de vista de clases, símbolos"
  - "símbolos gráficos"
  - "IntelliSense, iconos"
  - "iconos, IntelliSense"
  - "símbolos, iconos del Examinador de objetos"
  - "Examinador de objetos, iconos de la Vista de clases"
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Iconos de la Vista de clases y del Examinador de objetos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Vista de clases** y el **Explorador de objetos** muestran iconos que representan las entidades del código, por ejemplo, los espacios de nombres, las clases, las funciones y las variables.  La tabla siguiente muestra y describe los iconos.  
  
|Icono|Descripción|Icono|Descripción|  
|-----------|-----------------|-----------|-----------------|  
|![Símbolo de espacio de nombres](../ide/media/vxnamespace_icon.gif "vxNamespace\_Icon")|Espacio de nombres|![Símbolo de declaración](../ide/media/vxmethod_icon.png "vxMethod\_Icon")|Método o función|  
|![Icon Clase](../ide/media/vxclass_icon.png "vxClass\_Icon")|Clase|![Símbolo de operador](../ide/media/vxoperator_icon.png "vxOperator\_Icon")|Operador|  
|![Símbolo de la interfaz Lollipop](../ide/media/vxinterface_icon.png "vxInterface\_Icon")|Interfaz|![Símbolo de propiedad](../ide/media/vxproperty_icon.png "vxProperty\_Icon")|Propiedad.|  
|![Símbolo de estructura](../ide/media/vxstruct_icon.png "vxStruct\_Icon")|Estructura|![Icono Campo](../ide/media/vxfield_icon.png "vxField\_Icon")|Campo o variable|  
|![Símbolo de unión](../ide/media/vxunion_icon.png "vxUnion\_Icon")|Unión|![Símbolo de evento](../ide/media/vxevent_icon.png "vxEvent\_Icon")|Evento|  
|![Símbolo de enumeración](../ide/media/vxenum_icon.png "vxEnum\_Icon")|Enum|![Icono Constante](../ide/media/vxconstant_icon.png "vxConstant\_Icon")|Constante|  
|![Símbolo de definición de tipo](../ide/media/vxtypedef_icon.png "vxTypeDef\_Icon")|TypeDef|![Símbolo de elemento de enumeración](../ide/media/vxenumitem_icon.png "vxEnumItem\_Icon")|Elemento de tipo enumerado|  
|![Símbolo de módulo de Visual Studio](../ide/media/vxmodule_icon.gif "vxModule\_Icon")|Módulo|![Símbolo de elemento de mapa](../ide/media/vxmapitem_icon.png "vxMapItem\_Icon")|Elemento de mapa|  
|![Símbolo de método de extensión](../ide/media/extensionmethod.png "ExtensionMethod")|Método de extensión|![Símbolo de declaración](../ide/media/vxmethod_icon.png "vxMethod\_Icon")|Declaración externa|  
|![Símbolo de delegado](../ide/media/vxdelegate_icon.png "vxDelegate\_Icon")|Delegado|![Icono de error para Vista de clases y Examinador de objetos](../ide/media/erroricon.png "ErrorIcon")|Error|  
|![Símbolo de excepción](../ide/media/vxexception_icon.png "vxException\_Icon")|Excepción|![Símbolo de plantilla](../ide/media/vxtemplate_icon.png "vxTemplate\_Icon")|Plantilla|  
|![Símbolo de mapa](../ide/media/vxmap_icon.png "vxMap\_Icon")|Mapa|![Símbolo de error de punto de exclamación](../ide/media/vxerror_icon.png "vxError\_Icon")|Desconocido|  
|![Símbolo de reenvío de tipos](../ide/media/ob_type_forward.png "ob\_type\_forward")|Reenvío de tipo|||  
  
## Iconos de señal  
 Los iconos de señal siguientes se aplican a todos los iconos anteriores e indican su accesibilidad.  
  
> [!NOTE]
>  Si el proyecto está incluido en una base de datos de control de código fuente, es posible que aparezcan más iconos de señal para indicar el estado del control de código fuente, por ejemplo, protegido o desprotegido.  
  
|Icono|Descripción|  
|-----------|-----------------|  
|\<Sin icono de señal\>|Public.  Accesible desde cualquier lugar de este componente y desde cualquier componente que haga referencia a él.|  
|![Símbolo Protected de señal](../ide/media/vxsignal_icon_key.png "vxSignal\_Icon\_Key")|Protected  Accesible desde dentro del tipo o clase que lo contiene, o los derivados del tipo o clase que lo contiene.|  
|![Símbolo Private de señal](../ide/media/vxsignal_icon_lock.png "vxSignal\_Icon\_Lock")|Private  Accesible solamente desde el tipo o clase que lo contiene.|  
|![Símbolo Sealed de señal](../ide/media/vxsignal_icon_envelope.png "vxSignal\_Icon\_Envelope")|Sealed.|  
|![Símbolo Friend&#47;Internal de señal](../ide/media/vxsignal_icon_diamond.png "vxSignal\_Icon\_Diamond")|Amigo o interna.  Accesible sólo desde el proyecto.|  
|![Flecha de icono de señal](../ide/media/vxsignal_icon_arrow.gif "vxSignal\_Icon\_Arrow")|Shortcut.  Acceso directo al objeto.|  
  
## Vea también  
 [Ver la estructura del código](../ide/viewing-the-structure-of-code.md)