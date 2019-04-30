---
title: Introducción a las plantillas de proyecto de Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], about project templates
- Excel Workbook project template
- Word Template project template
- Excel [Office development in Visual Studio], project templates
- Project [Office development in Visual Studio], project templates
- project templates [Office development in Visual Studio]
- project templates, Word
- InfoPath [Office development in Visual Studio], project templates
- Excel Template project template
- project templates, 2007 Microsoft Office system
- project templates, Excel
- PowerPoint [Office development in Visual Studio], project templates
- Word [Office development in Visual Studio], Word project templates
- Office projects [Office development in Visual Studio], templates
- Excel projects in Visual Studio
- Word Document project template
- Visio [Office development in Visual Studio], project templates
- Word projects in Visual Studio
- Outlook [Office development in Visual Studio], project templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4e998b2367929f788ace5fb6a8de7fc5bb96c3e3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438774"
---
# <a name="office-project-templates-overview"></a>Introducción a las plantillas de proyecto de Office
  Las Microsoft Office Developer Tools en Visual Studio incluye plantillas de proyecto para crear los siguientes tipos de soluciones de Office:

- [Personalizaciones de nivel de documento](#DocLevel)

- [Complementos de VSTO](#AppLevel)

  Para obtener una comparación detallada de estos tipos de soluciones de Office, consulte [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

  Las plantillas de proyecto de Office están disponibles en el cuadro de diálogo **Nuevo proyecto** , bajo el nodo **Office** de los nodos de los lenguajes **Visual C#** y **Visual Basic** . Cada plantilla genera un proyecto con la configuración adecuada para la aplicación de destino, incluidas las referencias de ensamblado y la configuración de depuración.

  Cada proyecto proporciona archivos y código a modo de introducción a un tipo específico de solución. El código generado para cada proyecto incluye controladores de eventos de inicio y cierre. Puede agregar código a estos controladores de eventos para inicializar la solución cuando se cargue y para limpiarla cuando se descargue. Para obtener más información, consulte [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md) y [eventos en proyectos de Office](../vsto/events-in-office-projects.md).

> [!NOTE]
> Las herramientas de desarrollo de Office se incluyen con algunas ediciones de Visual Studio. Para obtener más información, consulte [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="DocLevel"></a> Personalizaciones de nivel de documento
 El nodo **Office** del cuadro de diálogo **Nuevo proyecto** proporciona las siguientes plantillas de proyecto como punto de partida para crear personalizaciones de documentos para Word y Excel:

- **Documento de VSTO de Word 2013 y 2016**

- **Plantilla de VSTO de Word 2013 y 2016**

- **Libro de VSTO de Excel 2013 y 2016**

- **Plantilla de VSTO de Excel 2013 y 2016**

- **Documento de VSTO de Word 2010**

- **Plantilla de VSTO de Word 2010**

- **Libro de VSTO de Excel 2010**

- **Plantilla de VSTO de Excel 2010**

  Las plantillas de proyecto de libro de Excel y documento de Word proporcionan código como punto de partida para crear una solución basada en un documento o un libro. En estos tipos de soluciones, el código se ejecuta sólo cuando el documento asociado se abre en Word o Excel.

  Las plantillas de proyecto Plantilla de Word y Plantilla de Excel se comportan de forma idéntica a las plantillas de proyecto Documento de Word y Libro de Excel. Sin embargo, las plantillas de proyecto Plantilla de Word y Plantilla de Excel simplifican la creación de nuevas copias locales de documentos o libros de la plantilla personalizada en su solución. Las características de su solución están disponibles en el nuevo documento que el usuario crea a partir de la plantilla.

> [!NOTE]
> Las plantillas de Word que hacen referencia a extensiones de código administrado no se pueden usar como complementos VSTO globales. No se llama al ensamblado si la plantilla se carga desde el directorio de inicio de Word. Para obtener más información, consulte [limitaciones de las plantillas globales y complementos de Excel (archivos .xla)](#Limitations)

 Para obtener información sobre cómo empezar en estos tipos de proyecto, vea los temas siguientes:

- [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)

- [Soluciones de Word](../vsto/word-solutions.md)

- [Soluciones de Excel](../vsto/excel-solutions.md)

- [Tutorial: Crear la primera personalización de nivel de documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)

- [Tutorial: Crear la primera personalización en el nivel de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)

## <a name="AppLevel"></a> Complementos de VSTO
 El nodo **Office/SharePoint** del cuadro de diálogo **Nuevo proyecto** proporciona las siguientes plantillas de proyecto como punto de partida para crear complementos de VSTO.

- **Complemento de VSTO de Excel 2013 y 2016**

- **Complemento de VSTO de InfoPath 2013**

- **Complemento de VSTO de Outlook 2013 y 2016**

- **Complemento de PowerPoint 2013 y 2016**

- **Complemento de Project 2013 y 2016**

- **Complemento de Visio 2013 y 2016**

- **Complemento de Word 2013 y 2016**

- **Complemento de Excel 2010**

- **Complemento de InfoPath 2010**

- **Complemento de Outlook 2010**

- **Complemento de PowerPoint 2010**

- **Complemento de Project 2010**

- **Complemento de Visio 2010**

- **Complemento de Word 2010**

  Al crear un proyecto que está basado en una de estas plantillas de proyecto, el código de la solución se ejecuta cuando se abre la aplicación asociada. A diferencia de los proyectos de nivel de documento, el código no está asociado a un documento único.

  Para obtener más información sobre cómo empezar con estos tipos de proyecto, vea los temas siguientes:

- [Empezar a programar complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)

- [Programar complementos VSTO](../vsto/programming-vsto-add-ins.md)

- [Tutorial: Crear el primer complemento VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Tutorial: Crear el primer complemento VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Tutorial: Crear el primer complemento VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Tutorial: Crear el primer complemento VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Tutorial: Crear el primer complemento VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

## <a name="document-vs-template-solutions"></a>Frente a soluciones de plantilla de documento
 Cuando se diseña una solución basada en un documento de Word o en un libro de Excel, se debe optar por el mejor método para poner el documento a disposición de los usuarios.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

 En algunas ocasiones, es posible que desee proporcionar una copia de un documento a cada usuario. En este caso, cree la solución utilizando un proyecto de documento de Word o de Excel.

 En otras ocasiones, quizá desee colocar una plantilla en un servidor para que cada usuario pueda abrirla (produciéndose de ese modo el evento) y guardar una copia local como un documento. En este caso, cree la solución utilizando un proyecto de plantilla de Word o de Excel.

## <a name="comparison"></a>Comparación
 La tabla siguiente resume las diferencias existentes entre documentos y plantillas.

|Documentos|Plantillas|
|---------------|---------------|
|Los usuarios pueden abrir y modificar un documento, salvo que esté configurado como de sólo lectura. Los cambios guardados se mantienen en el original.|Los usuarios pueden abrir una plantilla para crear una copia local como documento nuevo. No pueden modificar el original, salvo si tienen permisos especiales.|
|Cuando se abre, el documento produce el evento <xref:Microsoft.Office.Tools.Word.Document.Open> .|Cuando se abre, la plantilla produce el evento <xref:Microsoft.Office.Tools.Word.Document.New> .|

## <a name="Limitations"></a> Limitaciones de las plantillas globales y complementos de Excel (archivos .xla)
 Es posible que los documentos, los libros y las plantillas no funcionen correctamente como plantillas globales ni como complementos VSTO de Excel (archivos .xla).

## <a name="word-templates"></a>Plantillas de Word
 Cuando una plantilla de Microsoft Office Word tiene extensiones de código administradas, no se llama al ensamblado del proyecto si la plantilla se adjunta como plantilla global o se carga desde el directorio de inicio de Word. Además, el documento no reconoce el formato de una plantilla que forma parte de una solución de Office.

## <a name="excel-add-ins-xla-files"></a>Complementos de Excel (archivos .xla)
 No hay ningún proyecto de Office para crear un complemento VSTO de Excel (*.xla* archivo). Se pueden guardar libros como archivos .xla, pero no es una operación admitida y no es recomendable hacerlo. Si guarda un libro que tiene extensiones de código como administrado un **Microsoft Office Excel Add-In (\*.xla)** archivo, puede seleccionarlo en el **Add-Ins** cuadro de diálogo para aplicarlo a otro libro. En algunos casos, el código se ejecutará en el libro de destino después de que se aplica el complemento de VSTO, pero no se admite el uso de la solución de Office.

## <a name="see-also"></a>Vea también
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)
- [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Empezar a programar personalizaciones de nivel de documento para Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Empezar a programar personalizaciones de nivel de documento para Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Empezar a programar complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
