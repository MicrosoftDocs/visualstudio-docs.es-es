---
title: Selección y moneda en el IDE Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f580b7c8e1651dcbcd053476ae756399a0ac3482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705581"
---
# <a name="selection-and-currency-in-the-ide"></a>Selección y moneda en el IDE
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) mantiene información sobre los objetos seleccionados actualmente por los usuarios mediante el *contexto*de selección . Con el contexto de selección, VSPackages puede participar en el seguimiento de divisas de dos maneras:

- Mediante la propagación de información de moneda sobre los VSPackages al IDE.

- Mediante la supervisión de las selecciones actualmente activas de los usuarios dentro del IDE.

## <a name="selection-context"></a>Contexto de selección
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE realiza un seguimiento global de la moneda IDE en su propio objeto de contexto de selección global. En la tabla siguiente se muestran los elementos que componen el contexto de selección.

|Elemento|Descripción|
|-------------|-----------------|
|Jerarquía actual|Normalmente el proyecto actual; una jerarquía actual NULL indica que la solución en su conjunto es actual.|
|ItemID actual|El elemento seleccionado dentro de la jerarquía actual; cuando hay varias selecciones en una ventana de proyecto, puede haber varios elementos actuales.|
|Actual`SelectionContainer`|Contiene uno o varios objetos para los que la ventana Propiedades debe mostrar propiedades.|

 Además, el entorno mantiene dos listas globales:

- Una lista de identificadores de comandos de interfaz de usuario activos

- Una lista de tipos de elementos activos actualmente.

### <a name="window-types-and-selection"></a>Tipos de ventanas y selección
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organiza las ventanas en dos tipos generales:

- Ventanas de tipo jerarquía

- Ventanas de marco, como ventanas de herramientas y documentos

  El IDE realiza un seguimiento de la moneda de forma diferente para cada uno de estos tipos de ventana.

  La ventana de tipo de proyecto más común es el explorador de soluciones, que controla el IDE. Una ventana de tipo de proyecto realiza un seguimiento de la jerarquía global y ItemID del contexto de selección global y la ventana se basa en la selección del usuario para determinar la jerarquía actual. Para las ventanas de tipo de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>proyecto, el entorno proporciona el servicio global, a través del cual VSPackages puede supervisar los valores actuales de los elementos abiertos. La exploración de propiedades en el entorno está impulsada por este servicio global.

  Las ventanas de marco, por otro lado, utilizan DocObject dentro de la ventana de marco para insertar el valor SelectionContext (el trío hierarchy/ItemID/SelectionContainer). . Las ventanas <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> de marco utilizan el servicio para este propósito. DocObject solo puede insertar valores para el contenedor de selección, dejando los valores locales para hierarchy y ItemID sin cambios, como es típico de los documentos secundarios MDI.

### <a name="events-and-currency"></a>Eventos y Moneda
 Pueden producirse dos tipos de eventos que afectan a la noción de moneda del entorno:

- Eventos que se propagan al nivel global y cambian el contexto de selección de marco de ventana. Entre los ejemplos de este tipo de evento se incluye la apertura de una ventana secundaria MDI, una ventana de herramientas global o una ventana de herramientas de tipo proyecto que se está abrendo.

- Eventos que cambian los elementos rastreados dentro del contexto de selección de marco de ventana. Los ejemplos incluyen cambiar la selección dentro de un DocObject o cambiar la selección en una ventana de tipo de proyecto.

## <a name="see-also"></a>Vea también
- [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)
- [Comentarios para el usuario](../../extensibility/internals/feedback-to-the-user.md)
