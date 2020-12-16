---
title: Asistente para publicación (desarrollo de Office en Visual Studio)
description: Obtenga información sobre cómo puede usar el Asistente para publicación para copiar archivos de solución en una ubicación especificada, crear los archivos de manifiesto y crear un programa de instalación en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25821a0f245f2f0ed30fcbfb10137a772dd0dd01
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528009"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Asistente para publicación (desarrollo de Office en Visual Studio)
  Use el **Asistente para publicación** para copiar archivos de solución en una ubicación especificada, crear los archivos de manifiesto y crear un programa de instalación.

 Para obtener acceso a este asistente, en el menú **compilar** , elija **publicar** *solutionname*. También puede tener acceso al **Asistente para publicación** desde **Explorador de soluciones**. Abra el menú contextual del nodo del proyecto y, a continuación, elija **publicar**.

 En cada sección siguiente se describe una página del asistente.

## <a name="where-do-you-want-to-publish-the-application"></a>¿Dónde desea publicar la aplicación?
 **Especificar la ubicación para publicar esta aplicación** Obligatorio. La ubicación de publicación es el directorio en el que el **Asistente para publicación** copia los archivos de solución, como los manifiestos, los ensamblados, el certificado temporal y otros archivos de la compilación. Es necesario tener acceso de escritura a este directorio.

 Escriba la ubicación como una ruta de acceso de disco, un recurso compartido de archivos, un sitio FTP o una dirección URL de sitio web, o haga clic en el botón **examinar** para buscar la ubicación. La ruta de acceso puede tener estos formatos:

- Una ruta de acceso relativa o absoluta en formato estándar de Windows, como *C:\Deploy\MyApplication* o *\MyApplication*.

- Una ruta de acceso UNC (Convención de nomenclatura universal), como *\\ \ServerName\MyApplication \\*.

- Una dirección URL de un sitio web, como `http://www.contoso.com/MyApplication` .

  De forma predeterminada, la ubicación de publicación es *http://localhost/projectname/* si tiene IIS instalado o el directorio Publish \ si no tiene IIS instalado.

> [!NOTE]
> Hay más consideraciones si el equipo de destino está ejecutando Windows Vista. Debe ser administrador en el equipo de Windows Vista para utilizar la opción de publicación local. Además, la ubicación predeterminada siempre es el directorio *de \\ publicación* , independientemente de si tiene IIS instalado.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>¿Cuál es la ruta de instalación predeterminada en los equipos de los usuarios finales?
 La ruta de instalación es opcional. Puede establecer la ruta de instalación más adelante si lo prefiere. Para obtener más información, consulte [Cómo: cambiar la ruta de instalación de una solución de Office](/previous-versions/bb608626(v=vs.110)).

 La ruta de instalación es el directorio desde el que el usuario final instalará la personalización. También es la ruta de acceso que usará la solución para buscar actualizaciones. El **Asistente para publicación** no implementa la solución en esta ubicación, a menos que la ruta de acceso sea la misma que la especificada en el cuadro **especifique la ubicación para publicar esta aplicación** en la página anterior.

 **Desde un sitio web** Especifique la dirección URL que los usuarios finales van a seguir para instalar la solución.

 **Desde una ruta de acceso UNC o un recurso compartido de archivos** Especifique la ruta de acceso UNC que seguirán los usuarios finales para instalar la solución.

 **Desde un CD-ROM o DVD-ROM** Esta opción no requiere una ruta de instalación.

 Visual Studio no graba el CD o DVD. Debe copiar el resultado en un CD o DVD de forma manual.

## <a name="see-also"></a>Consulte también
- [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Página publicar, diseñador de proyectos &#40;desarrollo de Office en Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)