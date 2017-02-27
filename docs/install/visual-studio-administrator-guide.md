---
title: "Gu&#237;a del administrador de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "01/12/2017"
ms.prod: "visual-studio-dev15"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instalación de red, Visual Studio"
  - "Guía del administrador, Visual Studio"
  - "instalación de Visual Studio, guía del administrador"
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
caps.handback.revision: 68
---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017-rc"></a>Guía del administrador de Visual Studio para Visual Studio 2017 RC

Puede implementar Visual Studio en una red siempre y cuando cada equipo de destino cumpla los [requisitos mínimos de instalación](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). Para crear un recurso compartido de red, puede ejecutar el archivo de instalación con el modificador --layout (tal y como se describe en la página [Crear una instalación sin conexión de Visual Studio](create-an-offline-installation-of-visual-studio.md)) y, después, copiarlo desde la máquina local al recurso compartido de red.   

 Tenga en cuenta que las instalaciones que se realizan desde un recurso compartido de red "recordarán" la ubicación de la que proceden. Esto significa que, para reparar un equipo cliente, quizás sea necesario volver al recurso compartido de red desde el que se instaló el cliente. Elija cuidadosamente la ubicación de red para que esté disponible durante el tiempo que espera que los clientes de Visual Studio 2017 se ejecuten en su organización.  

 > [!IMPORTANT]
 > A pesar de que, en general, se admite el uso de Visual Studio 2017 RC en un entorno de producción, las cargas de trabajo y los componentes que aparecen marcados como "Versión preliminar" en la interfaz de usuario de instalación no son compatibles para usarlos en un entorno de producción.

## <a name="see-also"></a>Vea también
* [Instalar Visual Studio 2017 RC](install-visual-studio.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md)
* [Crear una instalación sin conexión de Visual Studio 2017 RC](create-an-offline-installation-of-visual-studio.md)
* [Cómo notificar un problema con Visual Studio 2017 RC](../ide/how-to-report-a-problem-with-visual-studio-2017.md)



<!--HONumber=Feb17_HO4-->


