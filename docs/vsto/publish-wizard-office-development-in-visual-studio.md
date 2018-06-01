---
title: Asistente para publicación (desarrollo de Office en Visual Studio)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2481557d1d75d64b5eb3f52f2755953ca344d323
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692725"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Asistente para publicación (desarrollo de Office en Visual Studio)
  Use la **Asistente para publicación** para copiar archivos de la solución en una ubicación especificada, crear los archivos de manifiesto y crear un programa de instalación.  
  
 Para tener acceso a este asistente, en la **compilar** menú, elija **publicar** *nombresolución*. También puede tener acceso a la **Asistente para publicación de** de **el Explorador de soluciones**. Abra el menú contextual del nodo de proyecto y, a continuación, elija **publicar**.  
  
 Cada sección describe una página del asistente.  
  
## <a name="where-do-you-want-to-publish-the-application"></a>¿Dónde desea publicar la aplicación?  
 **Especifique la ubicación para publicar esta aplicación**  
 Requerido. La ubicación de publicación es el directorio donde el **Asistente para publicación** copia los archivos de solución como los manifiestos, los ensamblados, los certificados temporales y otros archivos de la compilación. Es necesario tener acceso de escritura a este directorio.  
  
 Escriba la ubicación como una ruta de acceso de disco, el recurso compartido de archivos, el sitio FTP o la dirección URL del sitio web, o haga clic en el **examinar** botón para buscar la ubicación. La ruta de acceso puede estar en estos formatos:  
  
-   Una ruta de acceso relativa o absoluta en el estándar de Windows de formato, como *C:\Deploy\MyApplication* o *\MyApplication*.  
  
-   Una ruta de acceso de convención de nomenclatura Universal (UNC), como  *\\\ServerName\MyApplication\\*.  
  
-   Una dirección URL de un sitio web del sitio, como http://www.microsoft.com/MyApplication.  
  
 De forma predeterminada, la ubicación de publicación es *http://localhost/projectname/* si tiene IIS instalado, o el directorio publish\ si lo hace no tiene IIS instalado.  
  
> [!NOTE]  
>  Existen consideraciones más si el equipo de destino está ejecutando Windows Vista. Debe ser un administrador en el equipo de Windows Vista para usar la opción de publicación local. Además, la ubicación predeterminada es siempre el *publicar\\*  directorio, independientemente de si tiene IIS instalado.  
  
## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>¿Qué es la ruta de instalación predeterminada en equipos de usuarios finales?  
 La ruta de instalación es opcional. Puede establecer la ruta de instalación más adelante si lo prefiere. Para obtener más información, consulte [Cómo: cambiar la ruta de instalación de una solución de Office](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 La ruta de instalación es el directorio desde el que el usuario final instalará la personalización. También es la ruta de acceso que usará la solución para buscar actualizaciones. El **Asistente para publicación de** implementar la solución en esta ubicación, a menos que la ruta de acceso es el mismo que se introdujo en la **especificar la ubicación para publicar esta aplicación** cuadro en la página anterior.  
  
 **Desde un sitio Web**  
 Especifique la dirección URL que los usuarios finales seguirán para instalar la solución.  
  
 **Desde un recurso compartido de archivo o ruta de acceso UNC**  
 Especifique la ruta de acceso UNC que los usuarios finales seguirán para instalar la solución.  
  
 **Desde un CD-ROM o DVD-ROM**  
 Esta opción no requiere una ruta de instalación.  
  
 Visual Studio no grabar el CD o DVD. Debe copiar manualmente el resultado en un CD o DVD.  
  
## <a name="see-also"></a>Vea también  
 [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Panel publicar, Diseñador de proyectos &#40;desarrollo de Office en Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)  
  
  