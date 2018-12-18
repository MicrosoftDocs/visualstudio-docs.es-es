---
title: Archivos varios
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- builds [Visual Studio], miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], outside of containers
- files [Visual Studio], Miscellaneous Files folder
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0241f1e918b4c0022106059b0466a15559f2e84
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747738"
---
# <a name="miscellaneous-files"></a>Archivos varios
Tal vez desee usar los editores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para trabajar de forma independiente en los archivos de un proyecto o de una solución. Mientras la solución está abierta, se pueden abrir y modificar los archivos sin necesidad de agregarlos a soluciones o proyectos. Los archivos con los que desea trabajar independientemente de los contenedores reciben el nombre de archivos varios. Los archivos varios son externos a soluciones y proyectos, no se incluyen en compilaciones y no se pueden incluir en soluciones que estén bajo control de código fuente.

 Hay un gran número de razones por las que resulta de utilidad abrir archivos independientemente de un contenedor. Puede darse el caso de que desee ver un archivo mientras desarrolla una solución basada en un proyecto, pero que dicho archivo no sea fundamental para el desarrollo de la solución. Este es el caso de las notas o instrucciones de programación, los esquemas de base de datos y los fragmentos de código. Además, es posible que desee crear un archivo independiente.

 ![Proyectos de soluciones](../../ide/reference/media/projects_solutions_misc.gif)

 El Explorador de soluciones puede mostrar una carpeta Archivos varios para los archivos si las opciones de la carpeta se encuentran habilitadas. Las opciones pueden establecerse desde [Documentos, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/documents-environment-options-dialog-box.md). Después de haber cerrado uno de estos archivos, éste no se asociará a ninguna solución ni proyecto en particular a menos que haya una opción habilitada también para esto.

 La carpeta Archivos varios representa los archivos en forma de vínculos. Aunque esta carpeta no forme parte de la solución, cuando abra una solución, algunos o todos los archivos de esta carpeta que se abrieron la última vez que se cerró la solución volverán a abrirse, en función de los valores asignados a la carpeta.

> [!NOTE]
> Algunos de los archivos que no aparecen en la carpeta Archivos varios son archivos que no se pueden modificar en el IDE, como los archivos .zip y .doc. El IDE no realizará el seguimiento de los archivos que sólo se pueden modificar con un editor externo.


## <a name="commands-available-in-the-ide"></a>Comandos disponibles en el IDE
 Los menús, las barras de herramientas y los comandos que contienen varían en función del formato del archivo que abra. Cuando abra un archivo de texto, por ejemplo, aparecerá la barra de herramientas correspondiente al Editor de texto y sus comandos quedarán disponibles. Si después abre un archivo de esquema XML, aparecerá la barra de herramientas del mismo nombre. Mientras edita el esquema XML, no podrá disponer de los comandos de barra de herramientas del Editor de textos (o de la propia barra de herramientas). El esquema XML es la ventana activa y, como tal, tiene un contexto de selección actual. Cuando cambie de un archivo de proyecto a un archivo de la carpeta de archivos varios, desaparecerán todos los comando relacionados con el proyecto y sólo permanecerán aquellos que estén directamente relacionados con los archivos de la carpeta de archivos varios.

## <a name="folder-display-options"></a>Opciones de presentación de carpetas
 Puede establecer opciones de presentación para la carpeta Archivos varios de manera que ésta aparezca aunque no haya abierto ningún archivo de esta carpeta. El archivo de soluciones no administra una lista de archivos de la carpeta de archivos varios de manera permanente. Utiliza una característica opcional que le permite memorizar una lista de los archivos utilizados más recientemente por cada usuario.

## <a name="see-also"></a>Vea también

- [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)
- [Documentos, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/documents-environment-options-dialog-box.md)