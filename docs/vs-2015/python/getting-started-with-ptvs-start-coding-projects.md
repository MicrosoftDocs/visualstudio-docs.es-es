---
title: 'Introducción a PTVS: Comenzar a codificar (proyectos) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14b85e70-b9a8-415c-a307-8c8c316a0495
caps.latest.revision: 7
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 6c2edaa5f2b3ce152f11c681c3349c5952324818
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574072"
---
# <a name="getting-started-with-ptvs-start-coding-projects"></a>Introducción a PTVS: Comenzar a codificar (proyectos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Python Tools para Visual Studio (PTVS) le ayuda a administrar el código. 
 
 Puede ver estas instrucciones en un breve [vídeo de YouTube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
 Si usó Python anteriormente, ya sabe que el proyecto se define por la manera en que se estructuran los archivos en disco. Esto funciona a la perfección con proyectos normales de Python, pero cuando cuenta con más archivos (páginas web con JavaScript, pruebas unitarias y scripts de compilación), los sistemas de archivos pueden resultar un poco restrictivos. Visual Studio usa proyectos para conseguir tres cosas. 
 
- Identificar archivos críticos. Los archivos importantes son aquellos que se incorporan en un sistema de control de versiones (archivos de origen, recursos, etc.), pero no los archivos que se generan como resultado de la compilación. Los archivos importantes también son aquellos que se copian en otro equipo para que otra persona pueda trabajar en la aplicación. 
 
- Especificar cómo se deben usar archivos. Puede que tenga archivos que una herramienta necesite procesar cada vez que los archivos cambien. Los proyectos de Visual Studio pueden capturar esta información. 
 
- Definir los límites de los componentes. Si tiene varios componentes en la aplicación, puede colocar cada uno en un proyecto independiente. Estos podrían implementarse en servidores diferentes, compilarse con una configuración de depuración o compilación diferente o incluso escribirse en otro lenguaje compatible con Visual Studio, como C++ o Node.js. 
 
 Para ayudarle a comenzar, existen varias plantillas de proyecto. Si ya tiene código Python con el que le gustaría trabajar, el asistente De código existente le ayudará a crear un proyecto que incluya todos los archivos. Existen varios proyectos web para algunos marcos de trabajo populares. Hay disponibles más plantillas en el paquete de ejemplos de PTVS. Existen varias opciones para que las plantillas web proporcionadas funcionen con otros marcos de trabajo. La plantilla de aplicación de Python es un proyecto vacío y limpio. Hay un módulo para comenzar. 
 
 Visual Studio muestra los proyectos abiertos en la ventana del Explorador de soluciones, incluidos todos los archivos, las rutas de búsqueda y los entornos de Python. Para agregar elementos nuevos, seleccione la carpeta del proyecto y, en el menú contextual (presione el botón derecho del puntero), elija Agregar y, a continuación, Nuevo elemento. Puede seleccionar cualquier elemento del cuadro de diálogo, personalizar el nombre del elemento y agregar el elemento al proyecto. 
 
 Puede arrastrarlo y colocarlo en el Explorador de soluciones. Si ya copió archivos en la estructura de directorios del proyecto, puede elegir Mostrar todos los archivos en la parte superior del Explorador de soluciones. A continuación, puede seleccionar los elementos que desea agregar y, en el menú contextual, elegir Incluir en el proyecto. 
 
 Puede ver estas instrucciones en un breve [vídeo de YouTube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
## <a name="see-also"></a>Vea también 
 [Documentación Wiki](https://github.com/Microsoft/PTVS/wiki/Projects) [Introducción a PTVS y vídeos](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

