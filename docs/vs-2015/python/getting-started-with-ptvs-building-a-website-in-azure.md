---
title: 'Introducción a PTVS: compilación de un sitio web en Azure | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 61f8748a3874f32db9c235d03b6b7464bc5cecf1
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54783201"
---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>Introducción a PTVS: Compilar un sitio web en Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede empezar a compilar rápidamente un sitio web de Python en Azure.  
  
 Puede ver estas instrucciones en un breve [vídeo de YouTube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
 Comience con el cuadro de diálogo Nuevo proyecto... y, en proyectos de Python, elija el proyecto web Bottle.  Esta plantilla [Bottle](http://bottlepy.org/docs/dev/index.html) es un sitio de inicio basado en la [plataforma de Bootstrap](http://getbootstrap.com/).  Cuando cree el proyecto, Visual Studio le pedirá que instale las dependencias (en este caso, Bottle) en un entorno virtual.  Dado que está realizando la implementación en un sitio web de Azure, deberá agregar las dependencias a un entorno virtual para implementar los bits necesarios para el correcto funcionamiento del sitio.  También deberá basar su entorno en Python 2.7 o 3.4 de 32 bits.  Una vez creado el proyecto, presione F5 para iniciar la ejecución de su sitio localmente.  
  
 Es fácil probar el sitio en Azure.  Si no tiene una suscripción a Azure, puede usar [try.azurewebsites.net](https://trywebsites.azurewebsites.net/).  Este sitio ofrece una manera sencilla de probar Azure Websites durante una hora de cada vez con solo un inicio de sesión social.  No se necesita ninguna tarjeta de crédito.  Elija la plantilla Sitio vacío en la lista desplegable Cambiar idioma y elija Crear.  En "Trabajar con la aplicación web", elija Descargar perfil de publicación y guarde el archivo para usarlo con Visual Studio.  También puede realizar la implementación con GIT desde cualquier sistema operativo.  
  
 Vuelva a Visual Studio y al proyecto que creó.  Seleccione el nodo del proyecto en el Explorador de soluciones, elija el botón derecho del puntero y elija Publicar.  Si tiene una suscripción a Azure, puede hacer clic en los sitios web de Microsoft Azure en el cuadro de diálogo para administrar los sitios desde aquí.  Para este tutorial, seleccione Importar para importar el perfil de publicación que acaba de descargar.  Dado que el perfil de publicación tiene toda la información necesaria, puede elegir Publicar.  En unos segundos se abrirá una nueva ventana del explorador y el sitio se hospedará en vivo en la nube de Azure.  
  
 Los sitios web simples son sencillos, pero para obtener información sobre aplicaciones web de Azure más importantes, consulte el vídeo de [documentación exhaustiva](https://www.youtube.com/watch?v=WG3pGmoo8nE&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=10), así como otros de este canal (vínculo de la esquina superior derecha de la página de introducción o del vídeo, así como más abajo).  
  
 Puede ver estas instrucciones en un breve [vídeo de YouTube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
## <a name="see-also"></a>Vea también  
 [Documentación de la wiki](https://github.com/Microsoft/PTVS/wiki/Web-Project)   
 [Introducción y vídeos Deep Dive de PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
