---
title: Iconos de la vista de clases y del examinador de objetos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e67763234ff7b3778cccabaed45fbbc0bc04d30
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620480"
---
# <a name="class-view-and-object-browser-icons"></a>Iconos de la Vista de clases y del Examinador de objetos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Vista de clases** y el **Examinador de objetos** se muestran iconos que representan las entidades de código, por ejemplo, los espacios de nombres, las clases, las funciones y las variables. En la tabla siguiente se muestran y describen los iconos.

|Iconos|Descripción|Iconos|Descripción|
|----------|-----------------|----------|-----------------|
|![Símbolo de espacio de nombres](../ide/media/vxnamespace-icon.gif "vxNamespace_Icon")|Espacio de nombres|![Símbolo de declaración](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Método o función|
|![Icono de clase](../ide/media/vxclass-icon.gif "vxClass_Icon")|Clase|![Operador Symbol](../ide/media/vxoperator-icon.gif "vxOperator_Icon")|"??"|
|![Símbolo de la interfaz Lollipop](../ide/media/vxinterface-icon.gif "vxInterface_Icon")|Interfaz|![Símbolo de propiedad](../ide/media/vxproperty-icon.gif "vxProperty_Icon")|Propiedad.|
|![Símbolo de estructura](../ide/media/vxstruct-icon.gif "vxStruct_Icon")|Estructura|![Icono de campo](../ide/media/vxfield-icon.gif "vxField_Icon")|Campo o variable|
|![Símbolo de Unión](../ide/media/vxunion-icon.gif "vxUnion_Icon")|Unión|![Símbolo de evento](../ide/media/vxevent-icon.gif "vxEvent_Icon")|evento|
|![Símbolo de enumeración](../ide/media/vxenum-icon.gif "vxEnum_Icon")|Enum|![Icono constante](../ide/media/vxconstant-icon.gif "vxConstant_Icon")|Constante|
|![Símbolo de definición de tipo](../ide/media/vxtypedef-icon.gif "vxTypeDef_Icon")|TypeDef|![Enumerar símbolo de elemento](../ide/media/vxenumitem-icon.gif "vxEnumItem_Icon")|Elemento de enumeración|
|![Símbolo del módulo de Visual Studio](../ide/media/vxmodule-icon.gif "vxModule_Icon")|Module|![Símbolo de elemento de mapa](../ide/media/vxmapitem-icon.gif "vxMapItem_Icon")|Elemento de mapa|
|![Símbolo de método de extensión](../ide/media/extensionmethod.gif "ExtensionMethod")|Método de extensión|![Símbolo de declaración](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Declaración externa|
|![Símbolo de delegado](../ide/media/vxdelegate-icon.gif "vxDelegate_Icon")|delegado|![Icono de error de Vista de clases y Examinador de objetos](../ide/media/erroricon.gif "ErrorIcon")|Error|
|![Símbolo de excepción](../ide/media/vxexception-icon.gif "vxException_Icon")|Excepción|![Símbolo de plantilla](../ide/media/vxtemplate-icon.gif "vxTemplate_Icon")|Plantilla|
|![Símbolo de mapa](../ide/media/vxmap-icon.gif "vxMap_Icon")|Asignación|![Símbolo de signo de exclamación de error](../ide/media/vxerror-icon.gif "vxError_Icon")|Desconocido|
|![Símbolo de reenvío de tipos](../ide/media/ob-type-forward.gif "ob_type_forward")|Reenvío de tipos|||

## <a name="signal-icons"></a>iconos de señal
 Los siguientes iconos de señal se aplican a todos los iconos anteriores e indican su accesibilidad.

> [!NOTE]
> Si el proyecto se incluye en una base de datos de control de código fuente, es posible que se muestren más iconos de señal para indicar el estado de control de código fuente, como registrado o modificado.

|Iconos|Descripción|
|----------|-----------------|
|\<Icono Sin señal>|Público. Accesible desde cualquier lugar en este componente y desde cualquier componente que haga referencia a él.|
|![Símbolo de señal protegida](../ide/media/vxsignal-icon-key.gif "vxSignal_Icon_Key")|Protegido. Accesible desde la clase o el tipo contenedor o los derivados de la clase o el tipo contenedor.|
|![Símbolo privado de señal](../ide/media/vxsignal-icon-lock.gif "vxSignal_Icon_Lock")|Privado. Accesible solo en la clase o el tipo contenedor.|
|![Símbolo sellado de señal](../ide/media/vxsignal-icon-envelope.gif "vxSignal_Icon_Envelope")|Sellado.|
|![Símbolo interno&#47;de Signal Friend](../ide/media/vxsignal-icon-diamond.gif "vxSignal_Icon_Diamond")|Friend/interno. Accesible solo desde el proyecto.|
|![Flecha de icono de señal](../ide/media/vxsignal-icon-arrow.gif "vxSignal_Icon_Arrow")|Acceso directo. Un acceso directo al objeto.|

## <a name="see-also"></a>Vea también
 [Ver la estructura del código](../ide/viewing-the-structure-of-code.md)
