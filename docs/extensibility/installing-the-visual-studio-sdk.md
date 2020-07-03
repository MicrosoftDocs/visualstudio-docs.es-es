---
title: Instalación del SDK de Visual Studio | Microsoft Docs
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31df92b011336320d759461ed16ce2a3c8f61017
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905550"
---
# <a name="install-the-visual-studio-sdk"></a>Instalar Visual Studio SDK

El SDK de Visual Studio (kit de desarrollo de software) es una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalación del SDK de Visual Studio como parte de una instalación de Visual Studio

Para incluir el SDK de VS en la instalación de Visual Studio, instale la carga de trabajo **desarrollo de extensión de Visual Studio** en **otros conjuntos de herramientas**. Esta carga de trabajo instalará el SDK de Visual Studio y los requisitos previos necesarios. Puede ajustar aún más la instalación seleccionando o anulando la selección de componentes en la vista de **Resumen** .

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalación del SDK de Visual Studio después de instalar Visual Studio

Para instalar el SDK de Visual Studio después de completar la instalación de Visual Studio, vuelva a ejecutar el instalador de Visual Studio y seleccione la carga de trabajo **desarrollo de extensiones de Visual Studio** .

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Instalación del SDK de Visual Studio desde una solución

Si abre una solución con un proyecto de extensibilidad sin instalar primero el SDK de VS, se le pedirá un cuadro de diálogo **instalar característica que falta** para instalar la carga de trabajo **desarrollo de extensión de Visual Studio** :

![Instalar el desarrollo de extensiones](../extensibility/media/install-extension-development.png "Instalar el desarrollo de extensiones")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Instalación del SDK de Visual Studio desde la línea de comandos

Al igual que con cualquier carga de trabajo o componente de Visual Studio, también puede instalar la carga de trabajo **desarrollo de extensiones de Visual Studio** (ID.: Microsoft. VisualStudio. Workload. VisualStudioExtension) desde la línea de comandos. Vea [usar parámetros de línea de comandos para instalar Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) para obtener más información sobre los modificadores de línea de comandos adecuados y las instrucciones generales sobre cómo determinar la carga de trabajo o los identificadores de componente.

Tenga en cuenta que debe usar el instalador de Visual Studio que coincida con la versión instalada de Visual Studio. Por ejemplo, si tiene Visual Studio Enterprise instalado en el equipo, debe ejecutar el instalador de Visual Studio Enterprise (*vs_enterprise.exe*).
