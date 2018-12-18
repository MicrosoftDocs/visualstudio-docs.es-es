---
title: 'Cómo: configurar un equipo para desarrollar soluciones de Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6a07545fb9a7ddb2fc70ba5053ad131d2e214636
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671318"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Cómo: configurar un equipo para desarrollar soluciones de Office
  Para configurar un equipo de desarrollo de modo que puede usar las herramientas de desarrollo de Microsoft Office en Visual Studio, siga las instrucciones de este tema. Debe tener privilegios administrativos en el equipo de desarrollo para seguir estos pasos.  
  
### <a name="to-configure-the-development-computer"></a>Para configurar el equipo de desarrollo  
  
1.  Instala una versión de Visual Studio que incluye las herramientas para desarrolladores de Office. Office Developer Tools se instala de forma predeterminada. Si personaliza la instalación de Visual Studio y seleccionar las características que desea instalar, asegúrese de que **Microsoft Office Developer Tools** durante la instalación. Para obtener más información acerca de las versiones de Visual Studio que incluyen Office developer tools, consulte [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
2.  Instale una versión de Office que sea compatible con Office Developer Tools en Visual Studio. Para obtener más información, consulte [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
     Asegúrese de instalar también los PIA para la versión de Office que instale. De forma predeterminada, los PIA se instalan con Office. Si modifica la instalación de Office, asegúrese de que el **compatibilidad con programación de .NET** característica está seleccionada para las aplicaciones que desea establecer como destino.  
  
3.  Si tiene una versión en inglés de Visual Studio, pero usar configuración distinta del inglés para Windows, puede instalar el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] paquete de idioma para ver [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] mensajes en el mismo idioma que Windows. Las versiones de Visual Studio en otros idiomas instalan automáticamente el paquete de idioma. El paquete de idioma está disponible en el [centro de descarga de Microsoft](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Vea también  
 [Novedades de desarrollo de Office](https://msdn.microsoft.com/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Introducción a &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Cómo: instalar Visual Studio Tools para Office runtime redistribuible](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Cómo: ensamblados de interoperabilidad primarios de Office de instalación](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  