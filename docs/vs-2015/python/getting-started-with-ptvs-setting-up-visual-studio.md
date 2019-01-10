---
title: 'Introducción a PTVS: Configuración de Visual Studio 2015 | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec491c1d-bdb2-4c2b-a390-bd808cec635a
caps.latest.revision: 6
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 6ce34fb08edbad3c01594bfab770dffce1b82922
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852750"
---
# <a name="getting-started-with-ptvs-setting-up-visual-studio"></a>Introducción a PTVS: Configuración de Visual Studio

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La instalación de PTVS y las bibliotecas relacionadas es más rápida con Visual Studio. Si no tiene Visual Studio, puede obtener una copia gratuita de una versión de calidad profesional.

Puede ver estas instrucciones en un breve [vídeo de YouTube](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1).

Los pasos de alto niveles son los siguientes: instalar Visual Studio, instalar PTVS, instalar las bibliotecas de Python y los datos (Anaconda, Canopy) y, a continuación, por último, para comprobar la instalación.

Lo primero que necesitará es Visual Studio. Si eres un desarrollador individual o de código abierto, puede usar Visual Studio [Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs), que es gratuita y funcional para los profesionales de TI. También puede usar Community Edition en una organización, siempre y cuando sea para el aula de aprendizaje, la investigación académica o la participación en proyectos de código fuente. Los estudiantes y las startups deben informarse sobre los programas DreamSpark y BizSpark para comprobar si pueden tener acceso gratuito, o bien consultar al empresario si dispone de una suscripción a MSDN.

Una vez haya instalado Visual Studio, deberá [instalar PTVS](http://pytools.codeplex.com/wikipage?title=PTVS%20Installation). Se trata de una extensión independiente y gratuita, totalmente compatible con Microsoft y desarrollada en código abierto con las contribuciones de la comunidad.

Ahora debe [instalar Python](https://www.python.org/download/). Python está mantenido por la Comunidad y su página de inicio es python.org. Continuum Analytics genera un paquete gratuito llamado Anaconda que cuenta con Python y muchas bibliotecas útiles (especialmente para la ciencia y procesamiento de datos) y Enthought genera un paquete similar denominado Canopy. Solo necesita instalar uno de estos productos. Si no está seguro de cuál, comience con [Anaconda](https://www.continuum.io/downloads), que proporciona la versión de Python más actualizada y la mayoría de los paquetes de difícil instalación.

Inicie Visual Studio y asegúrese de que todo funciona. En el menú Ver, elija Otras ventanas. Verá un elemento denominado Entornos de Python. Esta ventana muestra todas las instalaciones de Python que detectó PTVS y todos los paquetes instalados. La ventana también controla la actualización de la base de datos para mostrar las finalizaciones mientras se edita código. Este proceso de actualización tarda algún tiempo, pero una vez que se hace PTVS puede mostrar más información acerca de los paquetes.

Si desea usar IPython con PTVS, siga estas [instrucciones](http://pytools.codeplex.com/wikipage?title=Using%20IPython%20with%20PTVS).

Puede ver estas instrucciones en un breve [vídeo de youtube](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1).

## <a name="see-also"></a>Vea también

[Introducción y vídeos Deep Dive de PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
