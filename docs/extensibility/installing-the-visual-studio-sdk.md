---
title: Instalación del SDK de Visual Studio ( Visual Studio SDK) Microsoft Docs
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f391708abbd8a9b66f2dfd5aaa6559cb075910d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710348"
---
# <a name="install-the-visual-studio-sdk"></a>Instalar Visual Studio SDK

El SDK de Visual Studio (Kit de desarrollo de software) es una característica opcional en la instalación de Visual Studio. También puede instalar el SDK de VS más adelante.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instale el SDK de Visual Studio como parte de una instalación de Visual Studio

Para incluir el SDK de VS en la instalación de Visual Studio, instale la carga de trabajo de desarrollo de **extensiones** de Visual Studio en **Otros conjuntos de herramientas**. Esta carga de trabajo instalará el SDK de Visual Studio y los requisitos previos necesarios. Puede ajustar aún más la instalación seleccionando o anulando la selección de componentes en la vista **Resumen.**

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Instale el SDK de Visual Studio después de instalar Visual Studio

Para instalar el SDK de Visual Studio después de completar la instalación de Visual Studio, vuelva a ejecutar el instalador de Visual Studio y seleccione la carga de trabajo de desarrollo de extensión de **Visual Studio.**

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Instale el SDK de Visual Studio desde una solución

Si abre una solución con un proyecto de extensibilidad sin instalar primero el SDK de VS, se le pedirá un cuadro de diálogo **Instalar característica que falta** para instalar la carga de trabajo de desarrollo de extensión de Visual **Studio:**

![Instalar el desarrollo de extensiones](../extensibility/media/install-extension-development.png "Instalar el desarrollo de extensiones")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Instale el SDK de Visual Studio desde la línea de comandos

Al igual que con cualquier carga de trabajo o componente de Visual Studio, también puede instalar la carga de trabajo de desarrollo de extensión de **Visual Studio** (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) desde la línea de comandos. Consulte [Usar parámetros de línea de comandos para instalar Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) para obtener más información sobre los modificadores de línea de comandos adecuados e instrucciones generales sobre cómo determinar los identificadores de carga de trabajo o componentes.

Tenga en cuenta que debe usar el instalador de Visual Studio que coincida con la versión instalada de Visual Studio. Por ejemplo, si tiene Visual Studio Enterprise instalado en el equipo, debe ejecutar el instalador de Visual Studio Enterprise (*vs_enterprise.exe*).
