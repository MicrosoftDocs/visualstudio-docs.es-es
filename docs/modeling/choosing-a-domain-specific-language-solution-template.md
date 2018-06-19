---
title: Elegir una plantilla de soluciones para lenguajes específicos de dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e0db20e4920f099882fd04d4ba06e65fb9c0c54c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949648"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Elegir una plantilla de soluciones para lenguajes específicos de dominio
Para crear una solución de lenguaje específico de dominio, elija una de las plantillas de solución que están disponibles en el Asistente para el Diseñador de lenguaje específico de dominio. Al elegir la plantilla que más se parezca al idioma que desea crear, puede minimizar las modificaciones que se deben realizar en la solución inicial.

 Las siguientes plantillas de solución están disponibles en el Asistente para el Diseñador de lenguaje específico de dominio.

|Plantilla|Características|Descripción|
|--------------|--------------|-----------------|
|Diagramas de clases|: Formas de compartimiento<br />: Herencia de clases<br />: Herencia de relaciones<br />: Herencia de la forma<br />: Propiedades de relación|Utilice esta plantilla de solución si su lenguaje específico de dominio incluye entidades y relaciones que tienen propiedades. Esta plantilla crea un lenguaje específico de dominio que se parezca a diagramas de clases UML. Las entidades principales son las clases e interfaces, junto con las relaciones de asociación, generalización y la implementación. Una clase o interfaz aparece como un cuadro que contiene una lista de atributos.|
|Diagrama de componentes|-Puertos|Utilice esta plantilla de solución si su lenguaje específico de dominio incluye componentes, es decir, partes de un sistema de software. Esta plantilla crea un lenguaje específico de dominio que se parezca a diagramas de componentes UML. Las entidades principales son componentes y puertos, que aparecen como formas pequeñas en la parte exterior de componentes.|
|Diagramas de flujo de tarea|-La imagen y formas de geometría<br />-   *Calles*|Utilice esta plantilla de solución si su lenguaje específico de dominio incluye los flujos de trabajo, Estados o secuencias. Esta plantilla crea un lenguaje específico de dominio que se parezca a diagramas de actividades UML. La entidad principal es una actividad y la relación principal es una transición entre actividades. La plantilla incluye otros elementos, como estado de inicio y estado final, una barra de sincronización.|
|Lenguaje mínima|-Una clase y forma<br />-Una relación y el conector|Utilice esta plantilla de solución si su lenguaje específico de dominio no se parece a las otras plantillas. Esta plantilla crea un lenguaje específico de dominio que tiene dos clases y una relación, que se representan en el **cuadro de herramientas** como **cuadro** y **línea**. La clase y la relación tienen una propiedad de cadena de ejemplo.|
|Diseñador de Windows Forms mínima|-Un modelo pequeño.<br />-Un formulario Windows Forms que muestra el modelo.|Utilice esta plantilla si desea crear una aplicación en el que está enlazado un DSL a un formulario Windows Forms, en lugar de un diseñador gráfico.<br /><br /> El formulario que actúa como la interfaz de usuario para el idioma está en la carpeta Dsl\UI.<br /><br /> Debe compilar el proyecto antes de abrir el Diseñador de formularios.<br /><br /> Para obtener más información, consulte [crear un lenguaje específico de dominio de Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Mínimo WPF Designer|-Un modelo pequeño<br />-Una interfaz de usuario de Windows Presentation Foundation que muestra el modelo|Utilice esta plantilla si desea crear una aplicación en el que está enlazado un DSL para una interfaz de usuario WPF, en lugar de un diseñador gráfico.<br /><br /> El Diseñador de la interfaz de usuario está en la carpeta Dsl\UI.<br /><br /> Debe compilar el proyecto antes de abrir el Diseñador de la interfaz de usuario.<br /><br /> Para obtener más información, consulte [crear un lenguaje específico de dominio de WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Biblioteca DSL|-Una biblioteca mínima|Utilice esta plantilla si desea crear una definición parcial de DSL que puede importarse en otras definiciones de DSL.|

## <a name="see-also"></a>Vea también

- [Información general sobre las herramientas de los lenguajes específicos de dominio](../modeling/overview-of-domain-specific-language-tools.md)
