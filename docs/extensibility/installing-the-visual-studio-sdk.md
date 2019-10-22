---
title: Instalar el SDK de Visual Studio | Microsoft Docs
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4208c20cc3e7da34efaf98af16f0f41d54613824
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340755"
---
# <a name="install-the-visual-studio-sdk"></a>Instalar Visual Studio SDK

Visual Studio SDK (Kit de desarrollo de Software) es una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalar el SDK de Visual Studio como parte de una instalación de Visual Studio

Para incluir el SDK de VS en la instalación de Visual Studio, instale el **desarrollo de extensiones de Visual Studio** carga de trabajo en **otros conjuntos de herramientas**. Esta carga de trabajo instalará el SDK de Visual Studio y los requisitos previos necesarios. Puede ajustar aún más la instalación seleccionando o anulando la selección de los componentes del **resumen** vista.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalar el SDK de Visual Studio después de instalar Visual Studio

Para instalar el SDK de Visual Studio después de completar la instalación de Visual Studio, vuelva a ejecutar el instalador de Visual Studio y seleccione el **desarrollo de extensiones de Visual Studio** carga de trabajo.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Instalar el SDK de Visual Studio desde una solución

Si abre una solución sin instalar primero el SDK de VS con un proyecto de extensibilidad, se le pedirá mediante un **instalar características que faltan** cuadro de diálogo para instalar el **desarrollo de extensiones de Visual Studio** carga de trabajo:

![Instalar el desarrollo de extensiones](../extensibility/media/install-extension-development.png "instalar el desarrollo de extensiones")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Instalar el SDK de Visual Studio desde la línea de comandos

Como con cualquier componente o carga de trabajo de Visual Studio, también puede instalar el **desarrollo de extensiones de Visual Studio** carga de trabajo (Id.: Microsoft.VisualStudio.Workload.VisualStudioExtension) desde la línea de comandos. Consulte [usar parámetros de línea de comandos para instalar Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) para obtener más información sobre los modificadores de línea de comandos adecuados y obtener instrucciones generales acerca de cómo determinar los identificadores de componente o carga de trabajo.

Tenga en cuenta que debe usar al instalador de Visual Studio que coincida con la versión instalada de Visual Studio. Por ejemplo, si tiene Visual Studio Enterprise instalado en el equipo, debe ejecutar el instalador de Visual Studio Enterprise (*vs_enterprise.exe*).