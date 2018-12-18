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
ms.openlocfilehash: d2977d546d463a8c21446a3643cff7ef49a01fb1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908845"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Elegir una plantilla de soluciones para lenguajes específicos de dominio
Para crear una solución de lenguaje específico de dominio, elija una de las plantillas de solución están disponibles en el Asistente para el Diseñador de lenguaje específico de dominio. Al elegir la plantilla que más se parezca el idioma que desea crear, puede minimizar las modificaciones que se deben realizar en la solución inicial.

 Las siguientes plantillas de solución están disponibles en el Asistente para el Diseñador de lenguaje específico de dominio.

|Plantilla|Características|Descripción|
|-|-|-|
|Diagramas de clases|-Formas de compartimiento<br />: Herencia de clases<br />: Herencia de relaciones<br />: Herencia de formas<br />: Las propiedades de relación|Utilice esta plantilla de solución si su lenguaje específico de dominio incluye entidades y relaciones que tienen propiedades. Esta plantilla crea un lenguaje específico de dominio que se parezca a diagramas de clases UML. Las entidades principales son las clases e interfaces, junto con las relaciones de asociación, generalización y la implementación. Una clase o interfaz aparece como un cuadro que contiene una lista de atributos.|
|Diagrama de componentes|: Puertos|Utilice esta plantilla de solución si su lenguaje específico de dominio incluye componentes, es decir, las partes de un sistema de software. Esta plantilla crea un lenguaje específico de dominio que se parezca a diagramas de componentes UML. Las entidades principales son los componentes y puertos, que aparecen como formas pequeñas en la parte exterior de los componentes.|
|Diagramas de flujo de tarea|-Imágenes y formas geométricas<br />-   *Calles*|Utilice esta plantilla de solución si su lenguaje específico de dominio incluye flujos de trabajo, Estados o secuencias. Esta plantilla crea un lenguaje específico de dominio que se parezca a diagramas de actividades UML. La entidad principal es una actividad, y la relación principal es una transición entre las actividades. La plantilla incluye otros elementos como estado de inicio, el estado final y una barra de sincronización.|
|Lenguaje mínimo|-Una clase y forma<br />-Una relación y conector|Use esta plantilla de solución si su lenguaje específico de dominio no se parece a las otras plantillas. Esta plantilla crea un lenguaje específico de dominio que tiene dos clases y una relación, que se representan en el **cuadro de herramientas** como **cuadro** y **línea**. La clase y la relación tienen una propiedad de cadena de ejemplo.|
|Diseñador de WinForm mínimo|-Un modelo pequeño.<br />-Un formulario de Windows que muestra el modelo.|Use esta plantilla si desea crear una aplicación en el que un DSL se enlaza a un formulario de Windows, en lugar de un diseñador gráfico.<br /><br /> El formulario que actúa como interfaz de usuario para el idioma está en la carpeta Dsl\UI.<br /><br /> Debe compilar el proyecto antes de abrir el Diseñador de formularios.<br /><br /> Para obtener más información, consulte [crear lenguajes específicos de dominio Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Minimal WPF Designer|-Un modelo pequeño<br />-Una interfaz de usuario de Windows Presentation Foundation que muestra el modelo|Use esta plantilla si desea crear una aplicación en el que está enlazado un DSL en una interfaz de usuario WPF, en lugar de un diseñador gráfico.<br /><br /> El Diseñador de la interfaz de usuario está en la carpeta Dsl\UI.<br /><br /> Debe compilar el proyecto antes de abrir el Diseñador de interfaz de usuario.<br /><br /> Para obtener más información, consulte [crear lenguajes específicos de dominio WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Biblioteca DSL|-Una biblioteca mínima|Use esta plantilla si desea crear una definición parcial de DSL que puede importarse en otras definiciones de DSL.|

## <a name="see-also"></a>Vea también

- [Información general sobre las herramientas de los lenguajes específicos de dominio](../modeling/overview-of-domain-specific-language-tools.md)
