---
title: Descripción general del desarrollo de soluciones de Office (VSTO)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: abb58d30e33ab5cfe713175b40cd32f593921ae9
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543949"
---
# <a name="office-solutions-development-overview-vsto"></a>Descripción general del desarrollo de soluciones de Office (VSTO)
  Mediante el uso de Microsoft Office como front-end de soluciones, puede beneficiarse de las conocidas interfaces de usuario y herramientas de Microsoft Office, como las características de procesamiento de texto de Word, las características de análisis de datos de Excel y las características de administración de correo electrónico de Outlook. Puede desarrollar soluciones en Visual Studio para personalizar las aplicaciones de Office y agregar las características específicas que necesite para sus procesos empresariales. Por ejemplo, puede convertir Word en un generador de contratos que ensamble contratos a partir de elementos previamente existentes que se pueden hacer modificables o no modificables. Con Excel puede crear una hoja de cálculo de presupuestos automatizada y personalizada para distintos proyectos. Los usuarios pueden aprovechar las soluciones de Office sin conexión, lo que hace que soluciones complejas resulten más prácticas de lo que serían si utilizase una arquitectura basada en web.

 Este tema proporciona información general sobre los tipos de soluciones de Office que puede crear mediante el uso de plantillas de Visual Studio Tools para Office (VSTO) disponibles en Office Developer Tools en Visual Studio. Para obtener información general sobre cómo desarrollar con Office, vea el [Centro para desarrolladores](https://developer.microsoft.com/office)de Office .

## <a name="choose-an-office-project-type"></a>Elija un tipo de proyecto de Office
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporciona los siguientes tipos de plantillas de proyecto para el desarrollo de Office basado en VSTO:

- Las**personalizaciones de nivel de documento** están asociadas a un documento concreto.

- **VSTO Add-ins** están asociados a la propia aplicación.

  Para decidir cuál de estos tipos de proyecto es mejor para su solución, piense si desea que su código se ejecute únicamente cuando se abra un documento específico o si desea que el código esté disponible cada vez que se ejecute la aplicación. Para obtener más información acerca de las plantillas de proyecto, vea [Introducción a las plantillas](../vsto/office-project-templates-overview.md)de proyecto de Office .

  Los tipos de proyectos que puede crear dependen de las aplicaciones de Office que haya instalado en el equipo de desarrollo. Para obtener más información, vea [Características disponibles por aplicación de Office y tipo](../vsto/features-available-by-office-application-and-project-type.md)de proyecto .

### <a name="document-level-customizations"></a>Personalizaciones de nivel de documento
 Las personalizaciones de nivel de documento constan de un ensamblado que está asociado a un único documento, libro o plantilla de Microsoft Office Word o Microsoft Office Excel. El ensamblado se carga cuando se abre el documento asociado. Las características de las personalizaciones que se crean están disponibles solo cuando se abre el documento asociado. Las personalizaciones no pueden realizar cambios en toda la aplicación, como mostrar un nuevo elemento de menú o una ficha de cinta cuando se abre cualquier documento.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incluye herramientas que le ayudan a crear personalizaciones de nivel de documento. El documento que se personaliza se hospeda como una superficie de diseño en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], lo que permite diseñar el documento arrastrando y colocando controles en él. Muchas otras características de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] están disponibles en proyectos de nivel de documento, como son los controles de Windows Forms, el enlace de datos con la función de arrastrar y colocar, y un depurador integrado.

 Para obtener más información sobre las personalizaciones, vea los siguientes temas:

- [Comience a programar personalizaciones de nivel de documento para Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [Comience a programar personalizaciones de nivel de documento para Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [Arquitectura de personalizaciones a nivel de documento](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>Complementos de VSTO
 Los complementos de VSTO constan de un ensamblado que está asociado a una aplicación de Microsoft Office. Normalmente, el complemento de VSTO se ejecuta cuando se inicia la aplicación asociada, aunque los usuarios también pueden cargar complementos de VSTO cuando la aplicación ya se está ejecutando. Las características de los complementos de VSTO que cree estarán disponibles para la propia aplicación, con independencia de qué documentos se abran.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]incluye herramientas para ayudarle a crear complementos de VSTO. Esta clase proporciona propiedades y eventos que puede utilizar para acceder al modelo de objetos de la aplicación host y ejecutar código cuando el complemento de VSTO se carga y se apaga. Muchas otras características de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] están disponibles en los proyectos de complementos de VSTO, como Windows Forms y un depurador integrado.

 Para obtener más información sobre complementos de VSTO, vea los siguientes temas:

- [Comience a programar complementos VSTO](../vsto/getting-started-programming-vsto-add-ins.md)

- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Automatice las aplicaciones de Office mediante ensamblados de interoperabilidad primarios
 Mediante programación, puede incorporar las características de una aplicación de Office en su solución escribiendo código que acceda al modelo de objetos de la aplicación. Los modelos de objetos son una disposición de clases que exponen funcionalidades a través de diversos métodos y propiedades. El modelo de objetos de cada aplicación de Office es diferente.

 Para utilizar el modelo de objetos de una aplicación de Office desde una solución creada con las herramientas de desarrollo de Office en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], debe utilizar el ensamblado de interoperabilidad primario (PIA) de la aplicación. El PIA permite al código administrado de una solución interactuar con el modelo de objetos basado en COM de la aplicación de Office.

 Para realizar la mayoría de las tareas de desarrollo, debe tener los PIA de Office instalados y registrados en la caché global de ensamblados del equipo de desarrollo. Para obtener más información, vea Configurar un equipo para desarrollar soluciones de [Office.](../vsto/configuring-a-computer-to-develop-office-solutions.md) Los PIA de Office no son obligatorios en los equipos de los usuarios finales para ejecutar soluciones de Office de VSTO. Para obtener más información, vea Diseñar y crear soluciones de [Office.](../vsto/designing-and-creating-office-solutions.md)

 Para obtener más información acerca de cómo utilizar los PIA en las soluciones de Office de VSTO, vea los siguientes temas:

- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)

- [ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Ejecutar soluciones de Microsoft VSTO Office en equipos de usuario final
 Al crear una solución de Office de VSTO, tenga en cuenta cómo pueden afectar los requisitos de implementación a las opciones de desarrollo.

### <a name="deployment-options"></a>Opciones de implementación
 Use ClickOnce o Windows Installer para implementar soluciones que cree mediante el uso de las herramientas de desarrollo de Office de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. La implementación mediante ClickOnce le permite crear soluciones de actualización automática que se pueden instalar y ejecutar con una mínima interacción por parte del usuario. Los archivos de Windows Installer (*.msi)* se pueden distribuir fácilmente a los equipos de usuario final o distribuirse mediante Systems Management Server (SMS). Para obtener más información acerca de la implementación de soluciones de VSTO Office, vea [Implementar una solución](../vsto/deploying-an-office-solution.md)de Office .

### <a name="install-prerequisites"></a>Requisitos previos de instalación
 Antes de que los usuarios finales puedan ejecutar una solución que haya creado mediante las herramientas de desarrollo de Office de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sus equipos deben disponer de ciertos requisitos previos. Si implementa su solución mediante ClickOnce o creando un archivo de Windows Installer, estos requisitos previos se pueden instalar con la solución. Para obtener más información, vea [Requisitos previos](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e) de la solución de Office para la implementación y [Cómo: Instalar requisitos previos en equipos de usuario final para ejecutar soluciones](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)de Office.

### <a name="security"></a>Seguridad
 La seguridad para las soluciones de Office de VSTO se ejecuta mediante una serie de comprobaciones que realiza [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] al instalar y cargar la solución. Estas comprobaciones incluyen comprobar si son de confianza la ubicación del manifiesto de implementación o el certificado que se ha usado para firmar este manifiesto. Para obtener más información, vea [Soluciones de Secure Office](../vsto/securing-office-solutions.md).

## <a name="see-also"></a>Vea también
- [Comience &#40;el desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Arquitectura de personalizaciones a nivel de documento](../vsto/architecture-of-document-level-customizations.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Comience a programar personalizaciones de nivel de documento para Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Comience a programar personalizaciones de nivel de documento para Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Comience a programar complementos VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
