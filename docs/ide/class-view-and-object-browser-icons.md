---
title: Iconos de la vista de clases y del examinador de objetos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f0a4371ae086e158f3fd7025e9867ffb99c92090
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2018
---
# <a name="class-view-and-object-browser-icons"></a>Iconos de la Vista de clases y del Examinador de objetos

En **Vista de clases** y **Examinador de objetos** se muestran iconos que representan las entidades de código, por ejemplo, los espacios de nombres, las clases, las funciones y las variables. En la tabla siguiente se muestran y describen los iconos.

|Iconos|Description|Iconos|Description|
|----------|-----------------|----------|-----------------|
|![Símbolo de espacio de nombres](../ide/media/vxnamespace_icon.gif "vxNamespace_Icon")|Espacio de nombres|![Símbolo de declaración](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Método o función|
|![Icono de clase](../ide/media/vxclass_icon.gif "vxClass_Icon")|Clase|![Símbolo de operador](../ide/media/vxoperator_icon.gif "vxOperator_Icon")|Operador|  
|![Símbolo de círculo de interfaz](../ide/media/vxinterface_icon.gif "vxInterface_Icon")|Interfaz|![Símbolo de propiedad](../ide/media/vxproperty_icon.gif "vxProperty_Icon")|Property|
|![Símbolo de estructura](../ide/media/vxstruct_icon.gif "vxStruct_Icon")|Estructura|![Icono de campo](../ide/media/vxfield_icon.gif "vxField_Icon")|Campo o variable|  
|![Símbolo de unión](../ide/media/vxunion_icon.gif "vxUnion_Icon")|Unión|![Símbolo de evento](../ide/media/vxevent_icon.gif "vxEvent_Icon")|evento|  
|![Símbolo de enumeración](../ide/media/vxenum_icon.gif "vxEnum_Icon")|Enum|![Icono de constante](../ide/media/vxconstant_icon.gif "vxConstant_Icon")|Constante|  
|![Símbolo de definición de tipo](../ide/media/vxtypedef_icon.gif "vxTypeDef_Icon")|TypeDef|![Símbolo de elemento de enumeración](../ide/media/vxenumitem_icon.gif "vxEnumItem_Icon")|Elemento de enumeración|  
|![Símbolo de módulo de Visual Studio](../ide/media/vxmodule_icon.gif "vxModule_Icon")|Module|![Símbolo de elemento de mapa](../ide/media/vxmapitem_icon.gif "vxMapItem_Icon")|Elemento de mapa|  
|![Símbolo de método de extensión](../ide/media/extensionmethod.gif "ExtensionMethod")|Método de extensión|![Símbolo de declaración](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Declaración externa|  
|![Símbolo de delegado](../ide/media/vxdelegate_icon.gif "vxDelegate_Icon")|delegado|![Icono de error de vista de clases y examinador de objetos](../ide/media/erroricon.gif "ErrorIcon")|Error|  
|![Símbolo de excepción](../ide/media/vxexception_icon.gif "vxException_Icon")|Excepción|![Símbolo de plantilla](../ide/media/vxtemplate_icon.gif "vxTemplate_Icon")|Plantilla|  
|![Símbolo de mapa](../ide/media/vxmap_icon.gif "vxMap_Icon")|Asignación|![Símbolo de signo de exclamación de error](../ide/media/vxerror_icon.gif "vxError_Icon")|Desconocido|  
|![Símbolo de reenvío de tipos](../ide/media/ob_type_forward.gif "ob_type_forward")|Reenvío de tipos|||  

## <a name="signal-icons"></a>Iconos de señal

Los siguientes iconos de señal se aplican a todos los iconos anteriores e indican su accesibilidad.

|Iconos|Description|
|----------|-----------------|  
|\<Icono Sin señal>|Público. Accesible desde cualquier lugar en este componente y desde cualquier componente que haga referencia a él.|  
|![Símbolo Protected de señal](../ide/media/vxsignal_icon_key.gif "vxSignal_Icon_Key")|Protegido. Accesible desde la clase o el tipo contenedor o los derivados de la clase o el tipo contenedor.|  
|![Símbolo Private de señal](../ide/media/vxsignal_icon_lock.gif "vxSignal_Icon_Lock")|Privado. Accesible solo en la clase o el tipo contenedor.|  
|![Símbolo Sealed de señal](../ide/media/vxsignal_icon_envelope.gif "vxSignal_Icon_Envelope")|Sellado.|  
|![Símbolo Friend&#47;Internal de señal](../ide/media/vxsignal_icon_diamond.gif "vxSignal_Icon_Diamond")|Friend/interno. Accesible solo desde el proyecto.|  
|![Flecha de icono de señal](../ide/media/vxsignal_icon_arrow.gif "vxSignal_Icon_Arrow")|Acceso directo. Un acceso directo al objeto.|

> [!NOTE]
> Si el proyecto se incluye en una base de datos de control de código fuente, es posible que se muestren más iconos de señal para indicar el estado de control de código fuente, como registrado o modificado.

## <a name="see-also"></a>Vea también

[Ver la estructura del código](../ide/viewing-the-structure-of-code.md)