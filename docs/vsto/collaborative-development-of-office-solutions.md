---
title: Desarrollo en colaboración de las soluciones de Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b4d22c92bd180eb27f8ebb50e65b24d17a92e47
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2018
ms.locfileid: "53441553"
---
# <a name="collaborative-development-of-office-solutions"></a>Desarrollo en colaboración de las soluciones de Office
  Varios desarrolladores pueden trabajar en un proyecto de Office en la misma manera que colaboran en otros proyectos de Visual Studio. Visual Studio localiza correctamente la instalación de Microsoft Office en cada equipo, incluso si está instalado Office en distintas ubicaciones. Sin embargo, hay algunas consideraciones importantes a tener en cuenta.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Depuración no se comparten las propiedades  
 Las propiedades de depuración no se comparten entre varios usuarios cuando se trabaja con control de código fuente. Proyectos de Visual Basic y Visual C# almacenan las propiedades de depuración en un archivo específico del usuario (*ProjectName*. vbproj.user o *ProjectName*. csproj.user), y este archivo no está bajo control de código fuente. Si hay más de una persona depurando, cada una debe introducir manualmente las propiedades de depuración.  
  
 Si el proyecto esté alojado en un recurso compartido de red en lugar de control de código fuente, se deben realizar algunos pasos adicionales para que los desarrolladores cooperadores abrir la solución y probar el ensamblado.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Control de código fuente requiere la retirada de todos los archivos  
 Si usa control de código fuente para los proyectos, debería consultar todos los archivos en un archivo de código en **el Explorador de soluciones** (como el *ThisDocument*, *ThisWorkbook*, o *ThisAddIn* archivos de código) cada vez que cambie el archivo de código, incluso los archivos que están ocultos de forma predeterminada. Si desprotege solo el archivo de código de nivel superior, podrían perderse los cambios.  
  
 Después de realizar los cambios, compruebe que todos los archivos de nuevo. Para obtener más información acerca de los archivos de código oculto en los proyectos, vea [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Seguridad para la colaboración en una red informal  
 Para todas las soluciones de nivel de documento que se encuentran en una ubicación de red (como \\ \\ *Servername*\\*Sharename*), la ubicación completa debe agregarse a la lista de carpetas de confianza en la aplicación de Microsoft Office que está trabajando. Seleccione la opción para incluir los subdirectorios bajo la carpeta principal, o específicamente agregue debug y carpetas a la lista de carpetas de confianza de compilación. Para obtener más información acerca de cómo hacerlo, consulte [conceder confianza a los documentos](../vsto/granting-trust-to-documents.md).  
  
 Los certificados temporales que se generan automáticamente en tiempo de compilación no están protegidos con contraseñas. Los certificados contienen el nombre de inicio de sesión del desarrollador y otra información personal. Si implementa las personalizaciones que están firmadas por certificados temporales, otras podrían estar puede tener acceso a esta información.  
  
## <a name="see-also"></a>Vea también  
 [Proteger soluciones de Office](../vsto/securing-office-solutions.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)  
  
  