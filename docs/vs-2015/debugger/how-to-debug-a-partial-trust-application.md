---
title: 'Cómo: depurar una aplicación de confianza parcial | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], partial trust applications
- partial trust applications
- security [Visual Studio], partial trust applications
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5880b375f15b189a2532ed750d87b95fea51f0df
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592733"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Cómo: Depurar una aplicación de confianza parcial
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: depurar una aplicación de confianza parcial](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-a-partial-trust-application).  
  
Se aplica a Windows y aplicaciones de consola.  
  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md) facilita la implementación de aplicaciones de confianza parcial que aprovechan las ventajas de [Code Access Security](http://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) para limitar el acceso a los recursos en un equipo.  
  
 La depuración de una aplicación de confianza parcial puede ser difícil porque estas aplicaciones tienen permisos de seguridad diferentes, por tanto, se comportan de manera diferente según la ubicación desde la que se instalen. Si una aplicación de confianza parcial se instala desde Internet, tendrá pocos permisos. Si se instala desde una intranet local, tendrá más permisos; si se instala desde el equipo local, tendrá todos los permisos. También puede haber zonas personalizadas con permisos personalizados. Tal vez sea necesario depurar una aplicación de confianza parcial si se cumple alguna de estas condiciones o todas ellas. Afortunadamente, Visual Studio también facilita esta tarea.  
  
 Antes de iniciar una sesión de depuración en Visual Studio, puede elegir la zona desde la cual simulará que se instaló la aplicación. Cuando se inicie la depuración, la aplicación tendrá los permisos correspondientes a una aplicación de confianza parcial instalada desde esa zona. Esto permite ver el comportamiento de la aplicación tal como lo verá un usuario que la descarga desde esa zona.  
  
 Si la aplicación intenta realizar una acción para la cual no tiene permiso, se inicia una excepción. En ese momento, el Asistente de excepciones de Visual Studio ofrece la opción de agregar un permiso adicional, lo que permite reiniciar la sesión de depuración con permisos suficientes para evitar el problema.  
  
 Después, es posible regresar y ver los permisos agregados durante la depuración. Si hubo que agregar un permiso durante la depuración, posiblemente haya que agregar una solicitud de consentimiento del usuario en esa parte del código.  
  
> [!NOTE]
>  Los visualizadores del depurador requieren más privilegios de los permitidos por una aplicación de confianza parcial. Los visualizadores no se cargarán cuando la ejecución se detenga en código con confianza parcial. Para depurar con un visualizador, debe ejecutar el código con plena confianza.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>Para elegir una zona para la aplicación de confianza parcial  
  
1.  Desde el **proyecto** menú, elija _Projectname_**propiedades**.  
  
2.  En el *Projectname* páginas de propiedades, haga clic en el **seguridad** página.  
  
3.  Seleccione **habilitar la configuración de seguridad de ClickOnce**.  
  
4.  En **zona desde la que se instalará la aplicación**, haga clic en el cuadro de lista desplegable y elija la zona que desea simular la aplicación se instala del.  
  
     El **los permisos requeridos por la aplicación** cuadrícula muestra todos los permisos disponibles. La marca de verificación indica los permisos concedidos a la aplicación.  
  
5.  Si la zona elegida es **(personalizada)**, seleccione la configuración personalizada correcta en el **configuración** columna de la **permisos** cuadrícula.  
  
6.  Haga clic en **Aceptar** para cerrar las páginas de propiedades.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>Para agregar un permiso adicional cuando se produce una excepción de seguridad  
  
1.  El **Asistente de excepciones** aparece el cuadro de diálogo con el mensaje: **se controló la excepción SecurityException.**  
  
2.  En el **Asistente de excepciones** cuadro de diálogo **acciones**, haga clic en **agregar permisos al proyecto**.  
  
3.  El **reiniciar depuración** aparece el cuadro de diálogo.  
  
    -   Si desea reiniciar la sesión de depuración con el nuevo permiso, haga clic en **Sí**.  
  
    -   Si no desea reiniciar todavía, haga clic en **No**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>Para ver permisos adicionales agregados durante la depuración  
  
1.  Desde el **proyecto** menú, elija _Projectname_**propiedades**.  
  
2.  En el *Projectname* páginas de propiedades, haga clic en el **seguridad** página.  
  
3.  Examine el **los permisos requeridos por la aplicación** cuadrícula. Los permisos adicionales agregados presentan dos iconos en el **incluidos** columna: la marca de verificación normal, que incluye todos los permisos y un icono adicional, que se parece a un globo que contiene la letra "i".  
  
4.  Use la barra de desplazamiento vertical para ver toda la **los permisos requeridos por la aplicación** cuadrícula.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)



