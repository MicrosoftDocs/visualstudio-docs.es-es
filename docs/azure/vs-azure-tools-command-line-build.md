---
title: Compilación de línea de comandos de Azure | Microsoft Docs
description: Compilación de línea de comandos de Azure
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: 64c18ea8b572d8481b2b2d04f8a8e16f21afc44a
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902505"
---
# <a name="building-azure-projects-from-the-command-line"></a>Compilación de proyectos de Azure desde la línea de comandos
Con Microsoft Build Engine (MSBuild) puede compilar productos en entornos de laboratorio de compilación en los que Visual Studio no está instalado. MSBuild utiliza un formato XML para archivos de proyecto que es ampliable y totalmente compatible con Microsoft. En este formato de archivo, puede describir los elementos que deben crearse en una o más plataformas y configuraciones.

También puede ejecutar MSBuild en una línea de comandos, enfoque que se describe en este tema. Estableciendo propiedades en un símbolo del sistema, puede crear configuraciones específicas de un proyecto. De forma similar, también puede definir los destinos que creará MSBuild. Para obtener más información sobre los parámetros de línea de comandos y MSBuild, consulte [Referencia de la línea de comandos de MSBuild](../msbuild/msbuild-command-line-reference.md).

## <a name="msbuild-parameters"></a>Parámetros de MSBuild
La manera más sencilla de crear un paquete consiste en ejecutar MSBuild con la opción `/t:Publish` . De manera predeterminada, este comando crea un directorio en relación con la carpeta raíz para el proyecto, por ejemplo, `<ProjectDirectory>\bin\Configuration\app.publish\`. Al compilar un proyecto de Azure, se generan dos archivos: el archivo del paquete y el archivo de configuración que lo acompaña:

* Archivo de paquete (`project.cspkg`)
* Archivo de configuración (`ServiceConfiguration.TargetProfile.cscfg`)

De manera predeterminada, cada proyecto de Azure incluye un archivo de configuración del servicio para las compilaciones locales (depuración) y otro para las compilaciones en la nube (ensayo o producción). Sin embargo, puede agregar o quitar archivos de configuración del servicio según sea necesario. Cuando compila un paquete dentro de Visual Studio, se le preguntará cuál archivo de configuración del servicio se debe incluir junto con el paquete. Cuando compila un paquete con MSBuild, el archivo de configuración del servicio local se incluye de manera predeterminada. Para incluir un archivo de configuración del servicio diferente, establezca la propiedad `TargetProfile` del comando de MSBuild (`MSBuild /t:Publish /p:TargetProfile=ProfileName`).

Si desea utilizar un directorio alternativo para el paquete y los archivos de configuración almacenados, establezca la ruta de acceso mediante la opción `/p:PublishDir=Directory\`, incluido el separador de barra diagonal inversa final.

## <a name="next-steps"></a>Pasos siguientes
Una vez compilado el paquete, puede implementarlo en Azure.
