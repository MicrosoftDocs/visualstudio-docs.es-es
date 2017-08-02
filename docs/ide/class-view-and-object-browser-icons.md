---
title: "Iconos de la Vista de clases y del Examinador de objetos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Iconos de la Vista de clases y del Examinador de objetos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Vista de clases** y el **Explorador de objetos** muestran iconos que representan las entidades del código, por ejemplo, los espacios de nombres, las clases, las funciones y las variables.  La tabla siguiente muestra y describe los iconos.  
  
|Icono|Descripción|Icono|Descripción|  
|-----------|-----------------|-----------|-----------------|  
|![Símbolo de espacio de nombres](~/docs/ide/media/vxnamespace_icon.gif "vxNamespace\_Icon")|Espacio de nombres|![Símbolo de declaración](~/docs/ide/media/vxmethod_icon.gif "vxMethod\_Icon")|Método o función|  
|![Icon Clase](~/docs/ide/media/vxclass_icon.gif "vxClass\_Icon")|Clase|![Símbolo de operador](~/docs/ide/media/vxoperator_icon.gif "vxOperator\_Icon")|Operador|  
|![Símbolo de la interfaz Lollipop](~/docs/ide/media/vxinterface_icon.gif "vxInterface\_Icon")|Interfaz|![Símbolo de propiedad](~/docs/ide/media/vxproperty_icon.gif "vxProperty\_Icon")|Propiedad.|  
|![Símbolo de estructura](~/docs/ide/media/vxstruct_icon.gif "vxStruct\_Icon")|Estructura|![Icono Campo](~/docs/ide/media/vxfield_icon.gif "vxField\_Icon")|Campo o variable|  
|![Símbolo de unión](~/docs/ide/media/vxunion_icon.gif "vxUnion\_Icon")|Unión|![Símbolo de evento](~/docs/ide/media/vxevent_icon.gif "vxEvent\_Icon")|Evento|  
|![Símbolo de enumeración](~/docs/ide/media/vxenum_icon.gif "vxEnum\_Icon")|Enum|![Icono Constante](~/docs/ide/media/vxconstant_icon.gif "vxConstant\_Icon")|Constante|  
|![Símbolo de definición de tipo](~/docs/ide/media/vxtypedef_icon.gif "vxTypeDef\_Icon")|TypeDef|![Símbolo de elemento de enumeración](~/docs/ide/media/vxenumitem_icon.gif "vxEnumItem\_Icon")|Elemento de tipo enumerado|  
|![Símbolo de módulo de Visual Studio](~/docs/ide/media/vxmodule_icon.gif "vxModule\_Icon")|Módulo|![Símbolo de elemento de mapa](~/docs/ide/media/vxmapitem_icon.gif "vxMapItem\_Icon")|Elemento de mapa|  
|![Símbolo de método de extensión](~/docs/ide/media/extensionmethod.gif "ExtensionMethod")|Método de extensión|![Símbolo de declaración](~/docs/ide/media/vxmethod_icon.gif "vxMethod\_Icon")|Declaración externa|  
|![Símbolo de delegado](~/docs/ide/media/vxdelegate_icon.gif "vxDelegate\_Icon")|Delegado|![Icono de error para Vista de clases y Examinador de objetos](~/docs/ide/media/erroricon.gif "ErrorIcon")|Error|  
|![Símbolo de excepción](~/docs/ide/media/vxexception_icon.gif "vxException\_Icon")|Excepción|![Símbolo de plantilla](~/docs/ide/media/vxtemplate_icon.gif "vxTemplate\_Icon")|Plantilla|  
|![Símbolo de mapa](~/docs/ide/media/vxmap_icon.gif "vxMap\_Icon")|Mapa|![Símbolo de error de punto de exclamación](~/docs/ide/media/vxerror_icon.gif "vxError\_Icon")|Desconocido|  
|![Símbolo de reenvío de tipos](~/docs/ide/media/ob_type_forward.gif "ob\_type\_forward")|Reenvío de tipo|||  
  
## Iconos de señal  
 Los iconos de señal siguientes se aplican a todos los iconos anteriores e indican su accesibilidad.  
  
> [!NOTE]
>  Si el proyecto está incluido en una base de datos de control de código fuente, es posible que aparezcan más iconos de señal para indicar el estado del control de código fuente, por ejemplo, protegido o desprotegido.  
  
|Icono|Descripción|  
|-----------|-----------------|  
|\<Sin icono de señal\>|Public.  Accesible desde cualquier lugar de este componente y desde cualquier componente que haga referencia a él.|  
|![Símbolo Protected de señal](~/docs/ide/media/vxsignal_icon_key.gif "vxSignal\_Icon\_Key")|Protected  Accesible desde dentro del tipo o clase que lo contiene, o los derivados del tipo o clase que lo contiene.|  
|![Símbolo Private de señal](~/docs/ide/media/vxsignal_icon_lock.gif "vxSignal\_Icon\_Lock")|Private  Accesible solamente desde el tipo o clase que lo contiene.|  
|![Símbolo Sealed de señal](~/docs/ide/media/vxsignal_icon_envelope.gif "vxSignal\_Icon\_Envelope")|Sealed.|  
|![Símbolo Friend&#47;Internal de señal](~/docs/ide/media/vxsignal_icon_diamond.gif "vxSignal\_Icon\_Diamond")|Amigo o interna.  Accesible sólo desde el proyecto.|  
|![Flecha de icono de señal](~/docs/ide/media/vxsignal_icon_arrow.gif "vxSignal\_Icon\_Arrow")|Shortcut.  Acceso directo al objeto.|  
  
## Vea también  
 [Ver la estructura del código](../ide/viewing-the-structure-of-code.md)