---
title: "Selecci&#243;n y moneda en el IDE | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "moneda, IDE de Visual Studio"
  - "IDE, selección"
  - "selección de IDE de Visual Studio"
  - "IDE, moneda"
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Selecci&#243;n y moneda en el IDE
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado \(IDE\) mantiene información sobre los usuarios objetos seleccionados mediante selección *contexto*. Con el contexto de selección, VSPackages pueden tomar parte en la moneda de seguimiento de dos maneras:  
  
-   Mediante la propagación de información de moneda sobre los VSPackages al IDE.  
  
-   Mediante la supervisión activa actualmente selecciones de los usuarios en el IDE.  
  
## Contexto de selección  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE globalmente realiza un seguimiento de moneda IDE en su propio objeto de contexto de selección global. En la tabla siguiente se muestra los elementos que componen el contexto de selección.  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|Jerarquía actual|Normalmente, el proyecto actual; una jerarquía actual de NULL indica que la solución como un todo está actualizada.|  
|Id. de elemento actual|El elemento seleccionado dentro de la jerarquía actual; Cuando hay varias selecciones en una ventana de proyecto, puede haber varios elementos actuales.|  
|Actual `SelectionContainer`|Contiene los objetos de uno o más para que la ventana de propiedades debe mostrar propiedades.|  
  
 Además, el entorno mantiene dos listas globales:  
  
-   Una lista de identificadores de comandos de interfaz de usuario activos  
  
-   Una lista de tipos de elemento activo actualmente.  
  
### Selección y tipos de ventana  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organiza windows en dos tipos:  
  
-   Ventanas de jerarquía  
  
-   Ventanas de marco, como ventanas de herramientas y documentos  
  
 El IDE realiza un seguimiento de moneda diferente para cada uno de estos tipos de ventana.  
  
 La ventana de tipo de proyecto más común es el Explorador de soluciones, que controla el IDE. Una ventana de tipo de proyecto realiza un seguimiento de la jerarquía global y el Id. de elemento del contexto de selección global y la ventana se basa en la selección del usuario para determinar la jerarquía actual. Para windows del tipo de proyecto, el entorno proporciona el servicio global <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, mediante los VSPackages puede supervisar los valores actuales de los elementos abiertos. Propiedad de navegación en el entorno está controlada por este servicio global.  
  
 Ventanas de marco, por otro lado, usar el DocObject dentro de la ventana de marco para insertar el valor de SelectionContext \(trío de Id. de elemento de jerarquía\/SelectionContainer\). . Ventanas de marco de usar el servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> para este propósito. El DocObject puede insertar sólo los valores para el contenedor de la selección, dejando los valores locales de la jerarquía y ItemID sin cambios, como es típico para documentos MDI secundarios.  
  
### Eventos y moneda  
 Pueden producirse dos tipos de eventos que afectan a la noción del entorno de moneda:  
  
-   Eventos que se propagan a nivel global y cambian el contexto de selección del marco de ventana. Ejemplos de este tipo de evento incluyen una ventana secundaria MDI se abre una ventana de herramientas global que se abre o se abre una ventana de herramientas de tipo de proyecto.  
  
-   Eventos que cambian los elementos que se realiza un seguimiento en el contexto de selección del marco de ventana. Por ejemplo, al cambiar la selección de DocObject o cambiar la selección en una ventana de tipo de proyecto.  
  
## Vea también  
 [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)   
 [Comentarios para el usuario](../../extensibility/internals/feedback-to-the-user.md)