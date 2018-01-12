---
title: "Cómo: configurar un equipo para desarrollar soluciones de Office | Documentos de Microsoft"
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
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a6f920bbc6ce2767728a08172243969b688f3ee9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Cómo: Configurar un equipo para desarrollar soluciones de Office
  Para configurar un equipo de desarrollo de modo que puede usar las herramientas de desarrollo de Microsoft Office en Visual Studio, siga las instrucciones de este tema. Debe tener privilegios administrativos en el equipo de desarrollo para seguir estos pasos.  
  
### <a name="to-configure-the-development-computer"></a>Para configurar el equipo de desarrollo  
  
1.  Instala una versión de Visual Studio que incluye las herramientas para desarrolladores de Office. Office Developer Tools se instala de forma predeterminada. Si personaliza la instalación de Visual Studio y selecciona las características que desea instalar, asegúrese de seleccionar **Microsoft Office Developer Tools** durante la instalación. Para obtener más información acerca de las versiones de Visual Studio que incluyen las herramientas de desarrollo de Office, consulte [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
2.  Instale una versión de Office que sea compatible con Office Developer Tools en Visual Studio. Para obtener más información, consulta [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
     Asegúrese de instalar también los PIA para la versión de Office que instale. De forma predeterminada, los PIA se instalan con Office. Si modifica la instalación de Office, asegúrese de que el **compatibilidad con programación de .NET** característica está seleccionada para las aplicaciones que desea tener como destino.  
  
3.  Si tiene una versión en inglés de Visual Studio pero usa configuración distinta del inglés para Windows, puede instalar el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] : paquete de idioma para ver [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] mensajes en el mismo idioma que Windows. Las versiones de Visual Studio en otros idiomas instalan automáticamente el paquete de idioma. El paquete de idioma está disponible en la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Vea también  
 [Novedades en el desarrollo de Office](http://msdn.microsoft.com/en-us/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Introducción a &#40; desarrollo de Office en Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Cómo: instalar Visual Studio Tools para Office Runtime redistribuible](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Cómo: Instalar ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  