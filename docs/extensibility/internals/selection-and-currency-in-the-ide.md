---
title: "Selección y moneda en el IDE | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e46c18f424130a29085aaccad19328c9f86682f6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="selection-and-currency-in-the-ide"></a>Selección y moneda en el IDE
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) mantiene información acerca de los usuarios los objetos actualmente seleccionados mediante el uso de selección *contexto*. Con el contexto de selección, paquetes VSPackage puede formar parte de la moneda de seguimiento de dos maneras:  
  
-   Mediante la propagación de información de moneda sobre los VSPackages al IDE.  
  
-   Mediante la supervisión de las selecciones actualmente activas de los usuarios desde el IDE.  
  
## <a name="selection-context"></a>Contexto de selección  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE global realiza un seguimiento de moneda IDE en su propio objeto de contexto de la selección global. En la tabla siguiente se muestra los elementos que componen el contexto de selección.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Jerarquía actual|Normalmente, el proyecto actual; una jerarquía actual de NULL indica que la solución como un todo está actualizada.|  
|ItemID actual|El elemento seleccionado dentro de la jerarquía actual; Cuando hay varias selecciones en una ventana del proyecto, puede haber varios elementos actuales.|  
|Actual`SelectionContainer`|Contiene los objetos de uno o más para que la ventana de propiedades debe mostrar las propiedades.|  
  
 Además, el entorno mantiene dos listas globales:  
  
-   Una lista de identificadores de comandos de interfaz de usuario activas  
  
-   Una lista de tipos de elemento activo actualmente.  
  
### <a name="window-types-and-selection"></a>Selección y tipos de ventana  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organiza windows en dos tipos generales:  
  
-   Windows de tipo de jerarquía  
  
-   Ventanas de marco, como las ventanas de herramientas y de documento  
  
 El IDE realiza un seguimiento de moneda diferente para cada uno de estos tipos de ventana.  
  
 La ventana de tipo de proyecto más común es el Explorador de soluciones, que controla el IDE. Una ventana de tipo de proyecto realiza un seguimiento de la jerarquía global y ItemID del contexto global de selección y la ventana se basa en la selección del usuario para determinar la jerarquía actual. Para las ventanas de tipo de proyecto, el entorno proporciona el servicio global <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>hasta qué VSPackages puede supervisar los valores actuales de los elementos abiertos. Propiedad examinar en el entorno está controlada por el servicio global.  
  
 Ventanas de marco, por otro lado, usar el DocObject dentro de la ventana de marco para insertar el valor de SelectionContext (la jerarquía/ItemID/SelectionContainer trio). . Ventanas de marco de usar el servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> para este propósito. Puede insertar el DocObject únicamente los valores para el contenedor de selección, dejando los valores locales para la jerarquía y ItemID no ha cambiado, tal y como es habitual para los documentos de elemento secundario MDI.  
  
### <a name="events-and-currency"></a>Eventos y moneda  
 Pueden producirse dos tipos de eventos que afectan a la noción del entorno de moneda:  
  
-   Eventos que se propagan a nivel global y cambian el contexto de selección del marco de ventana. Ejemplos de este tipo de evento incluyen una ventana secundaria MDI se abre una ventana de herramientas global se abre o se abre una ventana de herramientas de tipo de proyecto.  
  
-   Eventos que cambian los elementos que se realiza un seguimiento en el contexto de selección del marco de ventana. Por ejemplo, cambiar la selección de DocObject o selección en una ventana de tipo de proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)   
 [Comentarios para el usuario](../../extensibility/internals/feedback-to-the-user.md)