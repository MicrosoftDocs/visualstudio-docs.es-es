---
title: 'Cómo: depurar una aplicación de confianza parcial | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 030fef750cc1e0f0932de32fca1a0ffef56bc8f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704484"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Cómo: Depurar una aplicación de confianza parcial
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se aplica a Windows y aplicaciones de consola.  
  
 La [seguridad y la implementación de ClickOnce](../deployment/clickonce-security-and-deployment.md) facilitan la implementación de aplicaciones de confianza parcial que aprovechan la [seguridad de acceso del código](https://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) para limitar el acceso a los recursos de una máquina.  
  
 La depuración de una aplicación de confianza parcial puede ser difícil porque estas aplicaciones tienen permisos de seguridad diferentes, por tanto, se comportan de manera diferente según la ubicación desde la que se instalen. Si una aplicación de confianza parcial se instala desde Internet, tendrá pocos permisos. Si se instala desde una intranet local, tendrá más permisos; si se instala desde el equipo local, tendrá todos los permisos. También puede haber zonas personalizadas con permisos personalizados. Tal vez sea necesario depurar una aplicación de confianza parcial si se cumple alguna de estas condiciones o todas ellas. Afortunadamente, Visual Studio también facilita esta tarea.  
  
 Antes de iniciar una sesión de depuración en Visual Studio, puede elegir la zona desde la cual simulará que se instaló la aplicación. Cuando se inicie la depuración, la aplicación tendrá los permisos correspondientes a una aplicación de confianza parcial instalada desde esa zona. Esto permite ver el comportamiento de la aplicación tal como lo verá un usuario que la descarga desde esa zona.  
  
 Si la aplicación intenta realizar una acción para la cual no tiene permiso, se inicia una excepción. En ese momento, el Asistente de excepciones de Visual Studio ofrece la opción de agregar un permiso adicional, lo que permite reiniciar la sesión de depuración con permisos suficientes para evitar el problema.  
  
 Después, es posible regresar y ver los permisos agregados durante la depuración. Si hubo que agregar un permiso durante la depuración, posiblemente haya que agregar una solicitud de consentimiento del usuario en esa parte del código.  
  
> [!NOTE]
> Los visualizadores del depurador requieren más privilegios de los permitidos por una aplicación de confianza parcial. Los visualizadores no se cargarán cuando la ejecución se detenga en código con confianza parcial. Para depurar con un visualizador, debe ejecutar el código con plena confianza.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>Para elegir una zona para la aplicación de confianza parcial  
  
1. En el menú **proyecto** , elija _Projectname_**propiedades**de ProjectName.  
  
2. En las páginas de propiedades *projectname* , haga clic en la página **seguridad** .  
  
3. Seleccione **Habilitar la configuración de seguridad de ClickOnce**.  
  
4. En **zona desde la que se instalará la aplicación**, haga clic en el cuadro de lista desplegable y elija la zona desde la que desea simular la instalación de la aplicación.  
  
     Los **permisos requeridos por la cuadrícula de la aplicación** muestran todos los permisos disponibles. La marca de verificación indica los permisos concedidos a la aplicación.  
  
5. Si la zona elegida es **(personalizada)**, seleccione la configuración personalizada correcta en la columna **configuración** de la cuadrícula **permisos** .  
  
6. Haga clic en **Aceptar** para cerrar las páginas de propiedades.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>Para agregar un permiso adicional cuando se produce una excepción de seguridad  
  
1. Aparece el cuadro de diálogo **Asistente de excepciones** con el mensaje: **SecurityException no estaba controlado.**  
  
2. En el cuadro de diálogo **Asistente de excepciones** , en **acciones**, haga clic en **Agregar permiso al proyecto**.  
  
3. Aparecerá el cuadro de diálogo **reiniciar depuración** .  
  
    - Si desea reiniciar la sesión de depuración con el nuevo permiso, haga clic en **sí**.  
  
    - Si no desea reiniciar todavía, haga clic en **no**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>Para ver permisos adicionales agregados durante la depuración  
  
1. En el menú **proyecto** , elija _Projectname_**propiedades**de ProjectName.  
  
2. En las páginas de propiedades *projectname* , haga clic en la página **seguridad** .  
  
3. Observe los **permisos requeridos por la cuadrícula de la aplicación** . Cualquier permiso adicional que haya agregado tiene dos iconos en la columna **incluido** : la marca de verificación normal, que tienen todos los permisos incluidos, y un icono adicional, que es similar a un globo que contiene la letra "i".  
  
4. Use la barra de desplazamiento vertical para ver todos los **permisos requeridos por la cuadrícula de la aplicación** .  
  
## <a name="see-also"></a>Consulte también  
 [Seguridad e implementación de ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)
