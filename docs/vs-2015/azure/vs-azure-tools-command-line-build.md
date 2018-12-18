---
title: Compilación de línea de comandos de Azure | Microsoft Docs
description: Compilación de línea de comandos de Azure
author: ghogen
manager: douge
assetId: 94b35d0d-0d35-48b6-b48b-3641377867fd
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: fce752d91ebaa765e18efef117a3b6efe750119c
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002936"
---
# <a name="building-azure-projects-from-the-command-line"></a>Creación de proyectos de Azure desde la línea de comandos
Con Microsoft Build Engine (MSBuild), puede compilar productos en entornos de laboratorio de compilación donde no está instalado Visual Studio. MSBuild utiliza un formato XML para archivos de proyecto que ampliable y totalmente compatible con Microsoft. Con el formato de archivo de MSBuild, puede describir qué elementos se deben compilar en uno o más plataformas y configuraciones.

También puede ejecutar MSBuild en la línea de comandos, y el enfoque que se describe en este tema. Estableciendo propiedades en la línea de comandos, puede crear configuraciones específicas de un proyecto. De forma similar, también puede definir los destinos que creará MSBuild. Para obtener más información acerca de los parámetros de línea de comandos y MSBuild, consulte [referencia de línea de comandos de MSBuild](https://msdn.microsoft.com/library/ms164311.aspx).

## <a name="msbuild-parameters"></a>Parámetros de MSBuild
La manera más sencilla para crear un paquete consiste en ejecutar MSBuild con el `/t:Publish` opción. De forma predeterminada, este comando crea un directorio con respecto a la carpeta raíz del proyecto, como `<ProjectDirectory>\bin\Configuration\app.publish\`. Cuando compila un proyecto de Azure, se generan dos archivos: el archivo de paquete propio y el archivo de configuración complementario:

* Archivo de paquete (`project.cspkg`)
* Archivo de configuración (`ServiceConfiguration.TargetProfile.cscfg`)

De forma predeterminada, cada proyecto de Azure incluye un archivo de configuración del servicio para compilaciones (depuración) locales y otra para las compilaciones en la nube (ensayo o producción). Sin embargo, puede agregar o quitar archivos de configuración del servicio según sea necesario. Cuando se compila un paquete dentro de Visual Studio, se le pedirá qué archivo de configuración del servicio debe incluir junto con el paquete. Cuando compila un paquete con MSBuild, el archivo de configuración del servicio local se incluye de forma predeterminada. Para incluir un archivo de configuración del servicio diferente, establezca la `TargetProfile` propiedad del comando MSBuild (`MSBuild /t:Publish /p:TargetProfile=ProfileName`).

Si desea utilizar un directorio alternativo para el paquete almacenado y los archivos de configuración, establezca la ruta de acceso mediante el uso de la `/p:PublishDir=Directory\` opción, incluido el separador de barra diagonal inversa final.

## <a name="next-steps"></a>Pasos siguientes
Una vez compilado el paquete, puede implementarla en Azure.