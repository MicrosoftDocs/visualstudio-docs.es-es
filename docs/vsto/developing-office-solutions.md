---
title: Desarrollo de soluciones de Office
description: Obtenga información sobre cómo diseñar un proyecto con Office Developer Tools en Visual Studio. También aprenderá a empezar a implementar el código y la interfaz de usuario personalizada (UI).
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 012f08b4a4a8364d278322b7fe057231183fa233
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897589"
---
# <a name="develop-office-solutions"></a>Desarrollo de soluciones de Office
  Después de diseñar un proyecto con Office Developer Tools en Visual Studio y configurar los archivos del proyecto, puede empezar a centrarse en la implementación del código y la interfaz de usuario personalizada (UI).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="office-solutions-programming-model"></a>Modelo de programación de soluciones de Office
 El modelo de objetos de Office expone una variedad de objetos que se pueden programar. Cuando se programan soluciones de Office mediante código administrado, se escribe código que utiliza tipos de los ensamblados de interoperabilidad primarios de Office. En las soluciones que se crean mediante plantillas de proyecto de Office en Visual Studio, también se escribe código directamente relacionado con las clases generadas en el proyecto. Para obtener más información, vea [escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md).

## <a name="program-different-types-of-office-solutions"></a>Programar diferentes tipos de soluciones de Office
 El tipo de solución que esté creando determina las características que puede usar en el proyecto. Por ejemplo, puede agregar controles de formularios Windows Forms y controles de Office extendidos (denominados *controles host*) a las personalizaciones de nivel de documento, arrastrando para ello elementos desde el **cuadro de herramientas** de Visual Studio en tiempo de diseño. Sin embargo, si está desarrollando un complemento de VSTO, solo puede agregar este tipo de controles a los documentos en tiempo de ejecución, mediante la escritura de código.

 Para obtener más información acerca de las características específicas para cada tipo de solución, vea los temas siguientes:

- [Programas de complementos de VSTO](../vsto/programming-vsto-add-ins.md).

- [Personalizaciones de nivel de documento del programa](../vsto/programming-document-level-customizations.md).

- [Personalización](../vsto/office-ui-customization.md)de la interfaz de usuario de Office.

  Para obtener información general que le ayude a planear sus soluciones y procedimientos de Office para ayudarle a crear proyectos, consulte [diseño y creación de soluciones de Office](../vsto/designing-and-creating-office-solutions.md).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)|Describe distintos aspectos de la escritura de código en soluciones de Office.|
|[Complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md)|Proporciona información general sobre el modelo de programación de complementos de VSTO y las tareas de programación relacionadas.|
|[Personalizaciones de nivel de documento de programa](../vsto/programming-document-level-customizations.md)|Proporciona información general sobre el modelo de programación de personalizaciones de nivel de documento y las tareas de programación relacionadas.|
|[Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)|Describe las distintas formas de personalizar las aplicaciones de interfaz de usuario de Office mediante complementos de VSTO y personalizaciones de nivel de documento.|
|[Datos en soluciones de Office](../vsto/data-in-office-solutions.md)|Describe las distintas maneras de trabajar con datos en soluciones de Office, como enlazar datos a controles y almacenar datos en caché en las personalizaciones de nivel de documento.|
|[Cómo afecta autosave a las soluciones de Office](./how-autosave-impacts-office-solutions.md)|Describe los ajustes que puede tener que realizar en las soluciones de Office cuando está habilitado el guardado.|
|[Solucionar problemas de soluciones de Office](../vsto/troubleshooting-office-solutions.md)|Proporciona sugerencias para resolver problemas comunes que pueden surgir al crear soluciones de Office.|
|[Compatibilidad de subprocesos en Office](../vsto/threading-support-in-office.md)|Proporciona información general sobre cómo trabajar con varios subprocesos en soluciones de Office.|
|[Accesibilidad en proyectos de Office](../vsto/accessibility-in-office-projects.md)|Describe las características de accesibilidad que están disponibles en las soluciones de Office.|

## <a name="see-also"></a>Vea también
- [Cómo: crear y modificar propiedades de documento personalizadas](../vsto/how-to-create-and-modify-custom-document-properties.md)
- [Cómo: leer y escribir en propiedades de documento](../vsto/how-to-read-from-and-write-to-document-properties.md)
- [Cómo: elegir como destino la interfaz de usuario multilingüe de Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Tutorial: crear el primer complemento de VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)
- [Tutorial: crear la primera personalización de nivel de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Tutorial: crear el primer complemento de VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)
- [Tutorial: crear el primer complemento de VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Tutorial: crear el primer complemento de VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Tutorial: crear el primer complemento de VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)
- [Tutorial: crear la primera personalización de nivel de documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
