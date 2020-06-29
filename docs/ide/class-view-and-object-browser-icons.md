---
title: Iconos de la Vista de clases y del Examinador de objetos
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87bce70f83be2af80f93cf9888432257f6139732
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285156"
---
# <a name="class-view-and-object-browser-icons"></a>Iconos de la Vista de clases y del Examinador de objetos

En **Vista de clases** y **Examinador de objetos** se muestran iconos que representan las entidades de código, por ejemplo, los espacios de nombres, las clases, las funciones y las variables. En la tabla siguiente se muestran y describen los iconos.

|Iconos|Descripción|Iconos|Descripción|
|----------|-----------------|----------|-----------------|
|![Símbolo de espacio de nombres](../ide/media/vxnamespace_icon.gif)|Espacio de nombres|![Símbolo de declaración](../ide/media/vxmethod_icon.gif)|Método o función|
|![Icon Clase](../ide/media/vxclass_icon.gif)|Clase|![Símbolo de operador](../ide/media/vxoperator_icon.gif)|Operador|
|![Símbolo de la interfaz Lollipop](../ide/media/vxinterface_icon.gif)|Interfaz|![Símbolo de propiedad](../ide/media/vxproperty_icon.gif)|Propiedad.|
|![Símbolo de estructura](../ide/media/vxstruct_icon.gif)|Estructura|![Icono Campo](../ide/media/vxfield_icon.gif)|Campo o variable|
|![Símbolo de unión](../ide/media/vxunion_icon.gif)|Unión|![Símbolo de evento](../ide/media/vxevent_icon.gif)|evento|
|![Símbolo de enumeración](../ide/media/vxenum_icon.gif)|Enum|![Icono Constante](../ide/media/vxconstant_icon.gif)|Constante|
|![Símbolo de definición de tipo](../ide/media/vxtypedef_icon.gif)|TypeDef|![Símbolo de elemento de enumeración](../ide/media/vxenumitem_icon.gif)|Elemento de enumeración|
|![Símbolo de módulo de Visual Studio](../ide/media/vxmodule_icon.gif)|Module|![Símbolo de elemento de mapa](../ide/media/vxmapitem_icon.gif)|Elemento de mapa|
|![Símbolo de método de extensión](../ide/media/extensionmethod.gif)|Método de extensión|![Símbolo de declaración](../ide/media/vxmethod_icon.gif)|Declaración externa|
|![Símbolo de delegado](../ide/media/vxdelegate_icon.gif)|delegado|![Icono de error para Vista de clases y Examinador de objetos](../ide/media/erroricon.gif)|Error|
|![Símbolo de excepción](../ide/media/vxexception_icon.gif)|Excepción|![Símbolo de plantilla](../ide/media/vxtemplate_icon.gif)|Plantilla|
|![Símbolo de mapa](../ide/media/vxmap_icon.gif)|Asignación|![Símbolo de error de punto de exclamación](../ide/media/vxerror_icon.gif)|Desconocido|
|![Símbolo de reenvío de tipos](../ide/media/ob_type_forward.gif)|Reenvío de tipos|||

> [!TIP]
> Para ver mejor los iconos de esta página, asegúrese de que el tema Microsoft Docs está establecido en **Claro**. Puede alternar este tema de color desde el control que se encuentra en la parte inferior izquierda de la página, como se muestra en la siguiente captura de pantalla:
>
> ![Tema Docs](../ide/media/toggle-docs-color-theme.png "Alternar el tema de color para páginas de Microsoft Docs")

## <a name="signal-icons"></a>Iconos de señal

Los siguientes iconos de señal se aplican a todos los iconos anteriores e indican su accesibilidad.

|Iconos|Descripción|
|----------|-----------------|
|\<No Signal Icon>|Público. Accesible desde cualquier lugar en este componente y desde cualquier componente que haga referencia a él.|
|![Símbolo Protected de señal](../ide/media/vxsignal_icon_key.gif)|Protegido. Accesible desde la clase o el tipo contenedor o los derivados de la clase o el tipo contenedor.|
|![Símbolo Private de señal](../ide/media/vxsignal_icon_lock.gif)|Privado. Accesible solo en la clase o el tipo contenedor.|
|![Símbolo Sealed de señal](../ide/media/vxsignal_icon_envelope.gif)|Sellado.|
|![Símbolo Friend&#47;Símbolo interno](../ide/media/vxsignal_icon_diamond.gif)|Friend/interno. Accesible solo desde el proyecto.|
|![Flecha de icono de señal](../ide/media/vxsignal_icon_arrow.gif)|Acceso directo. Un acceso directo al objeto.|

> [!NOTE]
> Si el proyecto se incluye en una base de datos de control de código fuente, es posible que se muestren más iconos de señal para indicar el estado de control de código fuente, como registrado o modificado.

## <a name="see-also"></a>Vea también

- [Ver la estructura del código](../ide/viewing-the-structure-of-code.md)
