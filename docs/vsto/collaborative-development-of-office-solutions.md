---
title: Desarrollo en colaboración de las soluciones de Office
description: Obtenga información sobre cómo varios desarrolladores pueden trabajar en un proyecto de Office de la misma manera que colaboran en otros proyectos de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d30f28b3e97469bc9e0bf921438960206b4f89c0
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845809"
---
# <a name="collaborative-development-of-office-solutions"></a>Desarrollo en colaboración de las soluciones de Office
  Varios desarrolladores pueden trabajar en un proyecto de Office de la misma manera que colaboran en otros proyectos de Visual Studio. Visual Studio busca correctamente la instalación de Microsoft Office en cada equipo, incluso si Office se instala en ubicaciones diferentes. Sin embargo, hay algunas consideraciones importantes que debe tener en cuenta.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>Las propiedades de depuración no se comparten
 Las propiedades de depuración no se comparten entre varios usuarios cuando se trabaja con control de código fuente. Los proyectos de Visual Basic y Visual C# almacenan las propiedades de depuración en un archivo específico del usuario (*projectname*. vbproj. user o *nombreDeProyecto*. csproj. User), y este archivo no está bajo control de código fuente. Si hay más de una persona depurando, cada una debe introducir manualmente las propiedades de depuración.

 Si el proyecto está hospedado en un recurso compartido de red en lugar de en el control de código fuente, se deben realizar algunos pasos adicionales para permitir que los desarrolladores de colaboración abran la solución y prueben el ensamblado.

## <a name="source-control-requires-checking-out-all-files"></a>El control de código fuente requiere la desprotección de todos los archivos
 Si utiliza el control de código fuente para los proyectos, debe comprobar todos los archivos de un archivo de código en **Explorador de soluciones** (como los archivos de código *ThisDocument*, *ThisWorkbook* o *ThisAddIn* ) cada vez que cambie el archivo de código, incluso los archivos que están ocultos de forma predeterminada. Si desprotege solo el archivo de código de nivel superior, es posible que se pierdan los cambios.

 Después de realizar los cambios, vuelva a proteger todos los archivos. Para obtener más información sobre los archivos de código ocultos en los proyectos, vea [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="security-for-informal-collaboration-on-a-network"></a>Seguridad para la colaboración informal en una red
 En el caso de todas las soluciones de nivel de documento que se encuentran en una ubicación de red (como \\ \\ *ServerName* \\ *ShareName*), se debe agregar la ubicación completa a la lista de carpetas de confianza de la aplicación Microsoft Office con la que está trabajando. Seleccione la opción para incluir los subdirectorios en la carpeta principal, o bien agregue las carpetas de depuración y compilación a la lista de carpetas de confianza. Para obtener más información sobre cómo hacerlo, consulte [conceder confianza a los documentos](../vsto/granting-trust-to-documents.md).

 Los certificados temporales que se generan automáticamente en tiempo de compilación no están protegidos por contraseñas. Los certificados contienen el nombre de inicio de sesión del desarrollador y otra información personal. Si implementa personalizaciones que están firmadas por certificados temporales, es posible que otras personas puedan tener acceso a esta información.

## <a name="see-also"></a>Vea también
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Compilar soluciones de Office](../vsto/building-office-solutions.md)
