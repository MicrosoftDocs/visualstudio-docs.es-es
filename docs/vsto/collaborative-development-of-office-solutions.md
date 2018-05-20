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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9bf85dd1ba39df35e337f1b6b80099e3d5bcd774
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="collaborative-development-of-office-solutions"></a>Desarrollo en colaboración de las soluciones de Office
  Varios desarrolladores pueden trabajar en un proyecto de Office de la misma manera que colaboran en otros proyectos de Visual Studio. Visual Studio localiza correctamente la instalación de Microsoft Office en cada equipo, incluso si Office se instala en distintas ubicaciones. Sin embargo, hay algunas consideraciones importantes a tener en cuenta.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Depuración no se comparten propiedades  
 Las propiedades de depuración no se comparten entre varios usuarios cuando se trabaja con control de código fuente. Proyectos de Visual Basic y Visual C# almacenan las propiedades de depuración en un archivo específico del usuario (*ProjectName*. vbproj.user o *ProjectName*. csproj.user), y este archivo no está bajo control de código fuente. Si hay más de una persona depurando, cada una debe introducir manualmente las propiedades de depuración.  
  
 Si el proyecto se aloja en un recurso compartido de red en lugar de en el control de código fuente, deben realizarse algunos pasos adicionales para habilitar los desarrolladores colaborar para abrir la solución y probar el ensamblado.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Control de código fuente requiere la desprotección de todos los archivos  
 Si usa control de código fuente para los proyectos, debe comprobar todos los archivos en un archivo de código en **el Explorador de soluciones** (como el *ThisDocument*, *ThisWorkbook*, o *ThisAddIn* archivos de código) cada vez que cambie el archivo de código, incluso los archivos que están ocultos de forma predeterminada. Si desprotege el archivo de código de nivel superior, podrían perderse los cambios.  
  
 Después de realizar los cambios, compruebe que todos los archivos de nuevo. Para obtener más información acerca de los archivos de código oculto en los proyectos, vea [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Seguridad para la colaboración informal en una red  
 Para todas las soluciones de nivel de documento que se encuentran en una ubicación de red (como \\ \\ *Servername*\\*Sharename*), la ubicación completa debe agregarse a la lista de carpetas de confianza en la aplicación de Microsoft Office que está trabajando. Seleccione la opción para incluir los subdirectorios en la carpeta principal, o específicamente agregue debug y crear carpetas a la lista de carpetas de confianza. Para obtener más información acerca de cómo hacerlo, consulte [conceder confianza a los documentos](../vsto/granting-trust-to-documents.md).  
  
 Los certificados temporales que se generan automáticamente en tiempo de compilación no están protegidos por las contraseñas. Los certificados contienen el nombre de inicio de sesión del desarrollador y otra información personal. Si implementa personalizaciones firmadas por certificados temporales, otros usuarios puede tener acceso a esta información.  
  
## <a name="see-also"></a>Vea también  
 [Proteger soluciones de Office](../vsto/securing-office-solutions.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)  
  
  