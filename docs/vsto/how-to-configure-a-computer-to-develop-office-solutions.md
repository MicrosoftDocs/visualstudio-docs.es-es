---
title: 'Cómo: configurar un equipo para desarrollar soluciones de Office'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93c8287b0b2234c45056829ba78d993658b0428d
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585502"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Cómo: configurar un equipo para desarrollar soluciones de Office
  Para configurar un equipo de desarrollo de modo que puede usar las herramientas de desarrollo de Microsoft Office en Visual Studio, siga las instrucciones de este tema. Debe tener privilegios administrativos en el equipo de desarrollo para seguir estos pasos.

### <a name="to-configure-the-development-computer"></a>Para configurar el equipo de desarrollo

1. Instala una versión de Visual Studio que incluye las herramientas para desarrolladores de Office. Office Developer Tools se instala de forma predeterminada. Si personaliza la instalación de Visual Studio seleccionando las características que se van a instalar, asegúrese de que **Microsoft Office herramientas de desarrollo** esté seleccionado durante la instalación. Para obtener más información sobre las versiones de Visual Studio que incluyen las herramientas de desarrollo de Office, vea [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

2. Instale una versión de Office que sea compatible con Office Developer Tools en Visual Studio. Para obtener más información, vea [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

     Asegúrese de instalar también los PIA para la versión de Office que instale. De forma predeterminada, los PIA se instalan con Office. Si modifica la instalación de Office, asegúrese de que la característica **compatibilidad con programación de .net** esté seleccionada para las aplicaciones a las que desea dirigirse.

3. Si tiene una versión en Inglés de Visual Studio pero usa una configuración distinta del inglés para Windows, puede instalar el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] paquete de idioma para ver [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] los mensajes en el mismo idioma que Windows. Las versiones de Visual Studio en otros idiomas instalan automáticamente el paquete de idioma. El paquete de idioma está disponible en el [centro de descarga de Microsoft](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>Vea también

- [Introducción &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Cómo: instalar el Visual Studio Tools para Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Cómo: Instalar ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
