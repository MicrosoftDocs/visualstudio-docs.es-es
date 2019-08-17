---
title: Procedimiento Instalar el Visual Studio Tools para Office Runtime Redistributable
titleSuffix: ''
ms.custom: seodec18
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5d9bb53fbdc3d6766dab47c654f0a43ad902b2f3
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551840"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Procedimiento Instalar el Visual Studio Tools para Office Runtime Redistributable
  Visual Studio 2010 Tools para Office Runtime debe estar instalado en cada equipo que ejecute soluciones creadas con las herramientas de desarrollo de Microsoft Office en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. El runtime se instala de forma automática cuando se instala [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y Microsoft Office. Para obtener más información, vea [Visual Studio Tools para escenarios de instalación en tiempo de ejecución de Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 En las situaciones siguientes, deberá seguir las instrucciones de instalación manual que aparecen a continuación:

- Debe instalar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] en un servidor. Por ejemplo, desea utilizar la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para administrar las soluciones de nivel de documento en un servidor.

- Debe instalar el runtime en un equipo que ya tiene todos los otros requisitos previos para las soluciones de Office instaladas.

    > [!NOTE]
    > Tiene que ser administrador del equipo de desarrollo para instalar .NET Framework y [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Para instalar el runtime de Microsoft Visual Studio Tools para Office

1. Instale [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores.

    - Para descargar el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], consulte [Microsoft .NET Framework 4 (instalador Web)](http://go.microsoft.com/fwlink/?LinkId=178957).

    - Para descargar el [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], consulte [Microsoft .NET Framework 4 Client Profile (instalador Web)](http://go.microsoft.com/fwlink/?LinkId=178958).

    - Para descargar el [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consulte [Microsoft .NET Framework 4,5](http://www.microsoft.com/download/details.aspx?id=30653).

2. Ejecute *vstor_redist. exe* para instalar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

     Puede descargar estos archivos de instalación desde [Visual Studio 2010 Tools para Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384). Los requisitos previos para [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] coinciden con los requisitos previos para .NET Framework.

     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incluye paquetes de idioma. Si la instalación de Windows está establecida en un idioma distinto del inglés, puede mostrar los mensajes del runtime en el mismo idioma que se usa para Windows. De igual forma, si los usuarios finales instalan [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] y, a continuación, ejecutan sus soluciones en instalaciones de Windows que están establecidas en un idioma distinto del inglés, los mensajes del runtime aparecerán en el mismo idioma que Windows. En algunos casos, puede necesitar paquetes de idioma adicionales. Por ejemplo, podría necesitar paquetes de idioma adicionales si su copia de Windows usa más de una configuración de idioma, o si cambia a otro idioma después de haber instalado el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Puede encontrar paquetes de idioma en [Microsoft Visual Studio herramientas 2010 para el paquete de idioma del sistema Microsoft Office (versión 4,0 en tiempo de ejecución)](http://go.microsoft.com/fwlink/?LinkId=140386).

## <a name="see-also"></a>Vea también
- [Introducción &#40;al desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Procedimientos: Configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Procedimientos: Instalación de ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
