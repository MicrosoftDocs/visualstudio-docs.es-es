---
title: Elegir una plantilla de soluciones para lenguajes específicos de dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b76b61bb0ff84d3e1f0948057b60f6f3fbb505ad
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590571"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Elegir una plantilla de soluciones para lenguajes específicos de dominio
Para crear una solución de lenguaje específico de dominio, elija una de las plantillas de solución que están disponibles en el Asistente para Diseñador de lenguaje específico de dominio. Al elegir la plantilla que mejor se asemeja al idioma que desea crear, puede minimizar las modificaciones que debe realizar en la solución de inicio.

 Las siguientes plantillas de solución están disponibles en el Asistente para Diseñador de lenguaje específico de dominio.

|Plantilla|Características|Descripción|
|-|-|-|
|Diagramas de clases|-Formas de compartimiento<br />: Herencia de clases<br />-Herencia de relaciones<br />-Herencia de formas<br />-Propiedades de la relación|Use esta plantilla de solución si el lenguaje específico del dominio incluye entidades y relaciones que tienen propiedades. Esta plantilla crea un lenguaje específico del dominio similar a los diagramas de clases de UML. Las entidades principales son clases e interfaces, junto con relaciones de asociación, generalización e implementación. Una clase o interfaz aparece como un cuadro que contiene una lista de atributos.|
|Diagrama de componentes|Puertos de|Use esta plantilla de solución si su lenguaje específico de dominio incluye componentes, es decir, partes de un sistema de software. Esta plantilla crea un lenguaje específico de dominio similar a los diagramas de componentes de UML. Las entidades principales son componentes y puertos, que aparecen como pequeñas formas en el exterior de los componentes.|
|Diagramas de flujo de tareas|-Formas de imagen y geometría<br />-   *Swimlanes*|Use esta plantilla de solución si el lenguaje específico del dominio incluye flujos de trabajo, Estados o secuencias. Esta plantilla crea un lenguaje específico del dominio similar a los diagramas de actividades UML. La entidad principal es una actividad y la relación principal es una transición entre las actividades. La plantilla incluye varios otros elementos como el estado de inicio, el estado final y una barra de sincronización.|
|Lenguaje mínimo|-Una clase y una forma<br />-Una relación y un conector|Use esta plantilla de solución si el lenguaje específico de dominio no es similar al resto de plantillas. Esta plantilla crea un lenguaje específico del dominio que tiene dos clases y una relación, que se representan en el cuadro de **herramientas** como **Box** y **line**. La clase y la relación tienen cada una una propiedad de cadena de ejemplo.|
|Diseñador de WinForm mínimo|-Un modelo pequeño.<br />: Un Windows Form que muestra el modelo.|Use esta plantilla si desea compilar una aplicación en la que un DSL esté enlazado a un Windows Form, en lugar de un diseñador gráfico.<br /><br /> El formulario que actúa como la interfaz de usuario para el idioma está en la carpeta Dsl\UI.<br /><br /> Debe compilar el proyecto antes de abrir el diseñador de formularios.<br /><br /> Para obtener más información, vea [crear un lenguaje específico de dominio basado en Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|WPF Designer mínimo|-Un modelo pequeño<br />-Una Windows Presentation Foundation interfaz de usuario que muestra el modelo|Use esta plantilla si desea compilar una aplicación en la que un DSL esté enlazado a una interfaz de usuario de WPF, en lugar de un diseñador gráfico.<br /><br /> El diseñador de la interfaz de usuario está en la carpeta Dsl\UI.<br /><br /> Debe compilar el proyecto antes de abrir el diseñador de la interfaz de usuario.<br /><br /> Para obtener más información, vea [crear un lenguaje específico de dominio basado en WPF](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Biblioteca DSL|-Una biblioteca mínima|Use esta plantilla si desea crear una definición de DSL parcial que se pueda importar en otras definiciones de DSL.|

## <a name="see-also"></a>Vea también

- [Información general sobre las herramientas de los lenguajes específicos de dominio](../modeling/overview-of-domain-specific-language-tools.md)
