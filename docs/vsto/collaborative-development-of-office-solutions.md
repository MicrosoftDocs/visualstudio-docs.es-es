---
title: "Desarrollo en colaboración de las soluciones de Office | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3b69eccc3f6c140c44bff3b2d3d24e33914cae84
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="collaborative-development-of-office-solutions"></a>Desarrollo en colaboración de las soluciones de Office
  Varios desarrolladores pueden trabajar en un proyecto de Office de la misma manera que colaboran en otros proyectos de Visual Studio. Visual Studio localiza correctamente la instalación de Microsoft Office en cada equipo, incluso si Office se instala en distintas ubicaciones. Sin embargo, hay algunas consideraciones importantes a tener en cuenta.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Depuración no se comparten propiedades  
 Las propiedades de depuración no se comparten entre varios usuarios cuando se trabaja con control de código fuente. Proyectos de Visual Basic y Visual C# almacenan las propiedades de depuración en un archivo específico del usuario (*ProjectName*. vbproj.user o *ProjectName*. csproj.user), y este archivo no está bajo control de código fuente. Si hay más de una persona depurando, cada una debe introducir manualmente las propiedades de depuración.  
  
 Si el proyecto se aloja en un recurso compartido de red en lugar de en el control de código fuente, deben realizarse algunos pasos adicionales para habilitar los desarrolladores colaborar para abrir la solución y probar el ensamblado.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Control de código fuente requiere la desprotección de todos los archivos  
 Si usa control de código fuente para los proyectos, debe comprobar todos los archivos en un archivo de código en **el Explorador de soluciones** (por ejemplo, los archivos de código ThisAddIn, ThisWorkbook o ThisDocument) cada vez que cambie el archivo de código, incluso el archivos que están ocultos de forma predeterminada. Si desprotege el archivo de código de nivel superior, podrían perderse los cambios.  
  
 Después de realizar los cambios, compruebe que todos los archivos de nuevo. Para obtener más información acerca de los archivos de código oculto en los proyectos, vea [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Seguridad para la colaboración Informal en una red  
 Para todas las soluciones de nivel de documento que se encuentran en una ubicación de red (como \\ \\ *Servername*\\*Sharename*), la ubicación completa debe agregarse a la lista de carpetas de confianza en la aplicación de Microsoft Office que está trabajando. Seleccione la opción para incluir los subdirectorios en la carpeta principal, o específicamente agregue debug y crear carpetas a la lista de carpetas de confianza. Para obtener más información acerca de cómo hacerlo, consulte [otorgar confianza a los documentos](../vsto/granting-trust-to-documents.md).  
  
 Los certificados temporales que se generan automáticamente en tiempo de compilación no están protegidos por las contraseñas. Los certificados contienen el nombre de inicio de sesión del desarrollador y otra información personal. Si implementa personalizaciones firmadas por certificados temporales, otros usuarios puede tener acceso a esta información.  
  
## <a name="see-also"></a>Vea también  
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Compilación de soluciones de Office](../vsto/building-office-solutions.md)  
  
  