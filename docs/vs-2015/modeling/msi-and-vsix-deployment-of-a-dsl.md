---
title: Implementación de VSIX de un DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be9d3d44bfceaae1f2912086c3d20c90ce1e094b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916544"
---
# <a name="vsix-deployment-of-a-dsl"></a>Implementación de VSIX de un DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede instalar un lenguaje específico de dominio en su propio equipo o en otros equipos. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ya debe estar instalado en el equipo de destino.

## <a name="installing-and-uninstalling-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> Instalación y desinstalación de DSL mediante el uso de VSX
 Cuando este método instala DSL, el usuario puede abrir un archivo DSL desde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , pero el archivo no se puede abrir desde el explorador de Windows.

#### <a name="to-install-a-dsl-by-using-the-vsix"></a>Para instalar un DSL mediante el uso de VSIX

1. En el equipo, busque el archivo **. vsix** compilado por el proyecto de paquete DSL.

    1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto **DslPackage** y, a continuación, haga clic en **Abrir carpeta en el explorador de Windows**.

    2. Busque el archivo **bin \\ \* \\ **_YourProject_**. DslPackage. vsix**

2. Copie el archivo **. vsix** en el equipo de destino en el que desea instalar el DSL. Puede tratarse de su propio equipo o de otro.

    - El equipo de destino debe tener una de las ediciones de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] que admita DSL en tiempo de ejecución. Para obtener más información, consulte las [ediciones de Visual Studio compatibles con el SDK de modelado de & de visualización](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - El equipo de destino debe tener una de las ediciones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] especificadas en **DslPackage\source.Extensions.manifest**.

3. En el equipo de destino, haga doble clic en el archivo **. vsix** .

     El**Instalador de extensiones de Visual Studio** se abre e instala la extensión.

4. Inicie o reinicie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

5. Para probar el DSL, use [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para crear un nuevo archivo que tenga la extensión que definió para el DSL.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Para desinstalar un DSL que se instaló con VSX

1. En el menú **herramientas** , haga clic en **Administrador de extensiones**.

2. Expanda **Extensiones instaladas**.

3. Seleccione la extensión en la que se define el DSL y, a continuación, haga clic en **desinstalar**.

   En contadas ocasiones, una extensión defectuosa no se carga y crea un informe en la ventana de error, aunque no aparece en el Administrador de extensiones. En ese caso, puede quitar la extensión eliminando el archivo de:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**
