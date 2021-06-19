---
title: Elegir una plantilla de soluciones para lenguajes específicos de dominio
description: Aprenda a crear una solución de lenguaje específico de dominio eligiendo una de las plantillas de solución disponibles en el Asistente para diseñadores de lenguajes Domain-Specific lenguaje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c1c638c5a45427fd474f085ff58c9d38682ee054
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385440"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Elegir una plantilla de soluciones para lenguajes específicos de dominio
Para crear una solución de lenguaje específico de dominio, elija una de las plantillas de solución que están disponibles en el Asistente Domain-Specific diseñador de lenguajes. Al elegir la plantilla más parecida al lenguaje que desea crear, puede minimizar las modificaciones que tiene que realizar en la solución inicial.

 Las siguientes plantillas de solución están disponibles en el Asistente Domain-Specific diseñador de lenguajes.

|Plantilla|Características|Descripción|
|-|-|-|
|Diagramas de clases|- Formas de compartimiento<br />- Herencia de clases<br />- Herencia de relaciones<br />- Herencia de formas<br />- Propiedades de relación|Use esta plantilla de solución si el lenguaje específico del dominio incluye entidades y relaciones que tienen propiedades. Esta plantilla crea un lenguaje específico del dominio que se parece a los diagramas de clases UML. Las entidades principales son clases e interfaces, junto con relaciones de asociación, generalización e implementación. Una clase o interfaz aparece como un cuadro que contiene una lista de atributos.|
|Diagrama de componentes|- Puertos|Use esta plantilla de solución si el lenguaje específico del dominio incluye componentes, es decir, partes de un sistema de software. Esta plantilla crea un lenguaje específico del dominio similar a los diagramas de componentes UML. Las entidades principales son los componentes y puertos, que aparecen como formas pequeñas en el exterior de los componentes.|
|Diagramas de flujo de tareas|- Formas de imagen y geometría<br />-   *Calles*|Use esta plantilla de solución si el lenguaje específico del dominio incluye flujos de trabajo, estados o secuencias. Esta plantilla crea un lenguaje específico del dominio similar a los diagramas de actividad UML. La entidad principal es una actividad y la relación principal es una transición entre actividades. La plantilla incluye otros elementos, como el estado de inicio, el estado final y una barra de sincronización.|
|Lenguaje mínimo|- Una clase y forma<br />- Una relación y un conector|Use esta plantilla de solución si el lenguaje específico del dominio no se parece a las otras plantillas. Esta plantilla crea un lenguaje específico del dominio que tiene dos clases y una relación, que se representan en el cuadro de **herramientas** como **Box** y **Line**. La clase y la relación tienen una propiedad de cadena de ejemplo.|
|Diseñador mínimo de WinForm|- Un modelo pequeño.<br />- Windows Form que muestra el modelo.|Use esta plantilla si desea compilar una aplicación en la que un DSL esté enlazado a un Windows Forms, en lugar de a un diseñador gráfico.<br /><br /> El formulario que actúa como interfaz de usuario para el idioma se encuentra en la carpeta Dsl\UI.<br /><br /> Debe compilar el proyecto antes de abrir el diseñador de formularios.<br /><br /> Para obtener más información, [vea Creating a Windows Forms-Based Domain-Specific Language](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Diseñador wpf mínimo|- Un modelo pequeño<br />- Interfaz Windows Presentation Foundation usuario que muestra el modelo|Use esta plantilla si desea compilar una aplicación en la que un DSL esté enlazado a una interfaz de usuario de WPF, en lugar de a un diseñador gráfico.<br /><br /> El diseñador de la interfaz de usuario está en la carpeta Dsl\UI.<br /><br /> Debe compilar el proyecto antes de abrir el diseñador de interfaz de usuario.<br /><br /> Para obtener más información, vea [Creating a WPF-Based Domain-Specific Language](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Biblioteca DSL|- Una biblioteca mínima|Use esta plantilla si desea crear una definición de DSL parcial que se pueda importar en otras definiciones de DSL.|

## <a name="see-also"></a>Vea también

- [Información general sobre las herramientas de los lenguajes específicos de dominio](../modeling/overview-of-domain-specific-language-tools.md)
