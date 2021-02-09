---
title: Instalación del SDK de Visual Studio | Microsoft Docs
description: Obtenga información sobre las opciones para instalar el kit de desarrollo de software de Visual Studio, incluso durante la instalación de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5b0d239c2280362b45c085448437b15bd8ddfe8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869536"
---
# <a name="install-the-visual-studio-sdk"></a>Instalar Visual Studio SDK

El SDK (kit de desarrollo de software) de Visual Studio es una característica opcional del programa de instalación de Visual Studio. También puede instalar el SDK de VS después.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalación del SDK de Visual Studio como parte de una instalación de Visual Studio

Para incluir el SDK de VS en la instalación de Visual Studio, instale la carga de trabajo **Desarrollo de extensiones de Visual Studio** desde **Otros conjuntos de herramientas**. Esta carga de trabajo instalará el SDK de Visual Studio y los requisitos previos necesarios. Puede ajustar aún más la instalación si selecciona o anula la selección de componentes en la vista **Resumen**.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalación del SDK de Visual Studio después de instalar Visual Studio

Para instalar el SDK de Visual Studio después de completar la instalación de Visual Studio, vuelva a ejecutar el instalador de Visual Studio y seleccione la carga de trabajo **Desarrollo de extensiones de Visual Studio**.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Instalación del SDK de Visual Studio desde una solución

Si abre una solución con un proyecto de extensibilidad sin instalar primero el SDK de VS, se mostrará un cuadro de diálogo **Instalar la característica que falta** para que instale la carga de trabajo **Desarrollo de extensiones de Visual Studio**:

![Instalación del desarrollo de extensiones](../extensibility/media/install-extension-development.png "Instalación del desarrollo de extensiones")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Instalación del SDK de Visual Studio desde la línea de comandos

Como sucede con cualquier carga de trabajo o componente de Visual Studio, también puede instalar la carga de trabajo **Desarrollo de extensiones de Visual Studio** (id.: Microsoft.VisualStudio.Workload.VisualStudioExtension) desde la línea de comandos. Vea [Uso de parámetros de línea de comandos para instalar Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) para obtener más información sobre los modificadores de línea de comandos adecuados y las instrucciones generales sobre cómo determinar los identificadores de cargas de trabajo o componentes.

Tenga en cuenta que debe usar el instalador de Visual Studio que coincida con la versión instalada de Visual Studio. Por ejemplo, si ha instalado Visual Studio Enterprise en el equipo, debe ejecutar el instalador de Visual Studio Enterprise (*vs_enterprise.exe*).
