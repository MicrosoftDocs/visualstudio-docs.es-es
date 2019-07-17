---
title: Procedimiento Depurar una aplicación ClickOnce con permisos restringidos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ClickOnce applications
- ClickOnce deployment, debugging
- ClickOnce applications, debugging
ms.assetid: 6991ea91-5253-451b-923d-22273a3d38b1
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d60f88c4d1532a03922f12f21bb9b455ef5d84d8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153796"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Procedimiento Depurar una aplicación ClickOnce con permisos restringidos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Como desarrollador, probablemente esté ejecutando su equipo de desarrollo con permisos de plena confianza, por lo que no verá las mismas excepciones de seguridad al depurar una aplicación ClickOnce que las que podría ver el usuario final al ejecutarlo con permisos restringidos.  
  
 Para detectar estas excepciones, debe depurar la aplicación con los mismos permisos que el usuario final. Se puede habilitar la depuración con permisos restringidos en la página **Seguridad** del **Diseñador de proyectos**.  
  
 Además, al desarrollar aplicaciones que llaman a servicios web, dichos servicios suelen residir en el equipo de desarrollo. Una vez implementados, el usuario final tendrá acceso a estos servicios desde una dirección URL diferente. Para emular la experiencia del usuario final durante la depuración, puede especificar una dirección URL y el depurador tratará los servicios web como si se llamaran desde esa dirección URL.  
  
### <a name="to-enable-debugging-with-restricted-permissions"></a>Para habilitar la depuración con permisos restringidos  
  
1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2. En el **Diseñador de proyectos**, haga clic en la pestaña **Seguridad** .  
  
3. Active la casilla **Habilitar configuración de seguridad de ClickOnce** y haga clic en el botón de la opción **Aplicación de confianza parcial** .  
  
4. Haga clic en el botón **Avanzada** .  
  
5. Active la casilla **Depurar esta aplicación con el conjunto de permisos seleccionados** y haga clic en **Aceptar**.  
  
     Al depurar la aplicación, si intenta obtener acceso a un permiso que no forma parte del conjunto de permisos, se producirá una excepción de seguridad.  
  
### <a name="to-specify-a-url-for-debugging"></a>Para especificar una dirección URL para la depuración  
  
1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2. En el **Diseñador de proyectos**, haga clic en la pestaña **Seguridad** .  
  
3. Active la casilla **Habilitar configuración de seguridad de ClickOnce** y haga clic en el botón de la opción **Aplicación de confianza parcial** .  
  
4. Haga clic en el botón **Avanzada** .  
  
5. Active la casilla **Depurar esta aplicación con el conjunto de permisos seleccionados** y haga clic en **Aceptar**.  
  
6. En el cuadro de texto **Depurar esta aplicación como si se hubiera descargado de la siguiente dirección URL** , indique una dirección URL o una ruta de acceso a la red.  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)
