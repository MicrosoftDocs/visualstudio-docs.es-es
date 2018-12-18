---
title: Selección y moneda en el IDE | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45fc57bf2d5763527f9f8c2c6d8d22ca1d6369f8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786748"
---
# <a name="selection-and-currency-in-the-ide"></a>Selección y moneda en el IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE) mantiene información acerca de los usuarios los objetos actualmente seleccionados con selección *contexto*. Con el contexto de selección, VSPackages pueden tomar parte en la moneda de seguimiento de dos maneras:  
  
-   Mediante la propagación de información de moneda sobre los VSPackages para el IDE.  
  
-   Mediante la supervisión de las selecciones de los usuarios actualmente activo dentro del IDE.  
  
## <a name="selection-context"></a>Contexto de selección  
 El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE globalmente realiza un seguimiento de moneda IDE en su propio objeto de contexto de la selección global. La siguiente tabla muestra los elementos que componen el contexto de selección.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Jerarquía actual|Normalmente, el proyecto actual; una jerarquía actual de NULL indica que la solución como un todo está actualizada.|  
|ItemID actual|El elemento seleccionado dentro de la jerarquía actual; Cuando hay varias selecciones en una ventana de proyecto, puede haber varios elementos actuales.|  
|Actual `SelectionContainer`|Contiene los objetos de uno o más para que la ventana Propiedades debe mostrar las propiedades.|  
  
 Además, el entorno mantiene dos listas globales:  
  
-   Una lista de identificadores de comando de la interfaz de usuario activos  
  
-   Una lista de tipos de elemento activo actualmente.  
  
### <a name="window-types-and-selection"></a>Selección y tipos de ventana  
 El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE organiza windows en dos tipos generales:  
  
- Windows tipo de jerarquía  
  
- Ventanas de marco, como ventanas de herramientas y documentos  
  
  El IDE realiza un seguimiento de moneda diferente para cada uno de estos tipos de ventana.  
  
  La ventana de tipo de proyecto más común es el Explorador de soluciones, que controla el IDE. Una ventana de tipo de proyecto realiza un seguimiento de la jerarquía global e ItemID del contexto de selección global y la ventana se basa en la selección del usuario para determinar la jerarquía actual. Para windows de tipo de proyecto, el entorno proporciona el servicio global <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>hasta que los paquetes VSPackage pueden supervisar los valores actuales de los elementos abiertos. Propiedad en el entorno de exploración está controlado por este servicio global.  
  
  Ventanas de marco, por otro lado, usan el DocObject dentro de la ventana de marco para insertar el valor de SelectionContext (trío de la jerarquía/ItemID/SelectionContainer). . Uso de ventanas de marco del servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> para este propósito. Puede insertar el DocObject únicamente los valores para el contenedor de selección, dejar los valores locales para la jerarquía y ItemID sin cambios, como es típico para documentos de elemento secundario MDI.  
  
### <a name="events-and-currency"></a>Eventos y moneda  
 Podrían producirse dos tipos de eventos que afectan a la noción del entorno de moneda:  
  
-   Eventos que se propagan a nivel global y cambiar el contexto de selección del marco de ventana. Ejemplos de este tipo de evento incluyen una ventana secundaria MDI se abre una ventana de herramientas global que se abre o se abre una ventana de herramientas de tipo de proyecto.  
  
-   Eventos que cambian los elementos que se realiza un seguimiento en el contexto de selección de marco de ventana. Por ejemplo, cambiar la selección dentro de DocObject o cambiar la selección en una ventana de tipo de proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)   
 [Comentarios para el usuario](../../extensibility/internals/feedback-to-the-user.md)

