---
title: "Elegir una plantilla de solución de lenguaje específico de dominio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 24
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 2a1ad374c709b9575ff8e3d46bb3d2178a1c3f95
ms.lasthandoff: 02/22/2017

---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Elegir una plantilla de soluciones para lenguajes específicos de dominio
Para crear una solución de lenguaje específico de dominio, elija una de las plantillas de soluciones que están disponibles en el Asistente de diseñador de lenguaje específico de dominio. Al elegir la plantilla que más se parezca el idioma que desea crear, puede minimizar las modificaciones que realice en la solución inicial.  
  
 Las siguientes plantillas de solución están disponibles en el Asistente de diseñador de lenguaje específico de dominio.  
  
|Plantilla|Características|Descripción|  
|--------------|--------------|-----------------|  
|Diagramas de clases|: Formas de compartimiento<br />: Herencia de clases<br />: Herencia de relaciones<br />: Herencia de la forma<br />: Propiedades de relación|Utilice esta plantilla de solución si su lenguaje específico de dominio incluye las entidades y relaciones que tienen propiedades. Esta plantilla crea un lenguaje específico de dominio que se asemeja a diagramas de clases UML. Las entidades principales son las clases e interfaces, junto con las relaciones de asociación, generalización y la implementación. Una clase o interfaz aparece como un cuadro que contiene una lista de atributos.|  
|Diagrama de componentes|-Puertos|Utilice esta plantilla de solución si su lenguaje específico de dominio incluye componentes, es decir, partes de un sistema de software. Esta plantilla crea un lenguaje específico de dominio que se asemeja a diagramas de componentes UML. Las entidades principales son componentes y puertos que aparecen como pequeñas formas fuera de componentes.|  
|Diagramas de flujo de tarea|-Imágenes y formas geométricas<br />-   *Calles*|Utilice esta plantilla de solución si su lenguaje específico de dominio incluye flujos de trabajo, Estados o secuencias. Esta plantilla crea un lenguaje específico de dominio que se asemeja a diagramas de actividades UML. La entidad principal es una actividad y la relación principal es una transición entre actividades. La plantilla incluye varios otros elementos, como el estado de inicio, el estado final y una barra de sincronización.|  
|Lenguaje mínima|-Una clase y forma<br />-Una relación y el conector|Utilice esta plantilla de solución si su lenguaje específico de dominio no son similares a las otras plantillas. Esta plantilla crea un lenguaje específico de dominio que tiene dos clases y una relación, que se representan en el **herramientas** como **cuadro** y **línea**. La clase y la relación tienen una propiedad de cadena de ejemplo.|  
|Diseñador de WinForm mínimo|-Un modelo pequeño.<br />-Un formulario Windows Forms que muestra el modelo.|Use esta plantilla si desea crear una aplicación en el que está enlazado un DSL a un formulario Windows Forms, en lugar de un diseñador gráfico.<br /><br /> El formulario que actúa como interfaz de usuario para el idioma está en la carpeta Dsl\UI.<br /><br /> Debe compilar el proyecto antes de abrir el Diseñador de formularios.<br /><br /> Para obtener más información, consulte [crear lenguajes específicos de dominio Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|  
|Mínimo WPF Designer|-Un modelo pequeño<br />-Una interfaz de usuario de Windows Presentation Foundation que muestra el modelo|Use esta plantilla si desea crear una aplicación en el que está enlazado un DSL en una interfaz de usuario WPF, en lugar de un diseñador gráfico.<br /><br /> El Diseñador de la interfaz de usuario está en la carpeta Dsl\UI.<br /><br /> Debe compilar el proyecto antes de abrir el Diseñador de la interfaz de usuario.<br /><br /> Para obtener más información, consulte [crear lenguajes específicos de dominio WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|  
|Biblioteca DSL|-Una biblioteca mínima|Use esta plantilla si desea crear una definición parcial de DSL que puede importarse en otras definiciones de DSL.|  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre las herramientas de los lenguajes específicos de dominio](../modeling/overview-of-domain-specific-language-tools.md)

