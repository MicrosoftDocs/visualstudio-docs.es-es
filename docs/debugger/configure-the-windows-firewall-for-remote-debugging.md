---
title: Configurar el Firewall de Windows para la depuración remota | Documentos de Microsoft
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9fdd6db229bf1aa6f607e096715ea485ec5c5ce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465205"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Configurar el Firewall de Windows para la depuración remota
Este tema se describe cómo configurar el firewall para habilitar la depuración remota en equipos que ejecutan los sistemas operativos siguientes:  
  
-   Windows 10  
  
-   Windows 8/8.1  
  
-   Windows 7   
  
-   Windows Server 2012 R2  

-   Windows Server 2012
  
-   Windows Server 2008 R2 
  
 Si la red en la que está realizando la depuración no está protegida por un firewall, esta configuración no es necesaria. De lo contrario, el equipo que hospeda Visual Studio y el equipo remoto que se va a depurar requerirán cambios en la configuración del firewall.  
  
 **IPSec** Si la red requiere que la comunicación se realice con IPSec, debe abrir puertos adicionales en el equipo host de Visual Studio y en el equipo remoto.  
  
 **Servidor web** Si va a realizar la depuración de un servidor web remoto, debe abrir un puerto adicional en el equipo remoto. (Para IIS, el puerto 80 debe estar abierto.)  
  
 Tenga en cuenta que ambos equipos no tienen que ejecutar el mismo sistema operativo. Por ejemplo, el equipo de Visual Studio puede ejecutar Windows 10 y el equipo remoto puede ejecutar Windows Server 2012 R2.      
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Puertos en el equipo remoto que habilitan la depuración remota  
  
|||||  
|-|-|-|-|  
|**Puertos**|**Entrante/saliente**|**Protocolo**|**Descripción**|   
|4022|entrante|TCP|Para VS de 2017. El número de puerto se incrementa en 2 para cada versión de Visual Studio. Para obtener más información, consulte [Visual Studio remoto depurador las asignaciones de puertos](../debugger/remote-debugger-port-assignments.md).|  
|4023|entrante|TCP|Para VS de 2017. El número de puerto se incrementa en 2 para cada versión de Visual Studio. (Solo usado para remoto depurar un proceso de 32 bits de la versión de 64 bits del depurador remoto.) Para obtener más información, consulte [Visual Studio remoto depurador las asignaciones de puertos](../debugger/remote-debugger-port-assignments.md).| 
|3702|Saliente|UDP|(Opcional) Se requiere para la detección del depurador remoto.|    
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Cómo configurar puertos en el Firewall de Windows  

Cuando se instala Visual Studio o el depurador remoto, el software intentará abrir los puertos correctos. Sin embargo, en algunos escenarios (como el uso de un firewall de terceros), debe abrir un puerto manualmente. Si tiene que comprobar que los puertos estén abiertos, vea [solución de problemas](#troubleshooting). Algunas instrucciones para abrir un puerto pueden ser diferentes en versiones anteriores de Windows.

Para abrir un puerto:
  
1. Abra la **iniciar** menú, busque **Firewall de Windows con seguridad avanzada**.

2. A continuación, elija **reglas de entrada > nueva regla > puerto**y, a continuación, haga clic en **siguiente**. (Para reglas de salida, elija **reglas de salida** en su lugar.)

3. Elija **TCP** o **UDP**, según el número de puerto.

4. En **puertos locales específicos**, escriba el número de puerto, haga clic en **siguiente**.

5. Haga clic en **Allow the Connection** y, a continuación, haga clic en **Siguiente**.

6. Seleccione uno o más tipos de red desea habilitar para el puerto y haga clic en **siguiente**.

    Los tipos seleccionados deben incluir la red a la que está conectado el equipo remoto.
7. Agregue el nombre (por ejemplo, **msvsmon**, **IIS**, o **Web Deploy**) para la regla y haga clic en **finalizar**.

    Debería ver la nueva regla en la lista de reglas de entrada o las reglas de salida.

## <a name="troubleshooting"></a>Solución de problemas

Si tiene problemas para asociar a la aplicación con el depurador remoto, debe comprobar que estén abiertos los puertos correctos.

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-visual-studio-computer"></a>Compruebe que los puertos estén abiertos en el Firewall de Windows en el equipo de Visual Studio  
 Las instrucciones para configurar el firewall de Windows varían ligeramente en los distintos sistemas operativos. En Windows 8/8.1, Windows 10 y Windows Server 2012, la palabra **aplicación** se usa; en Windows 7 o Windows Server 2008, la palabra **programa** se usa;  En los pasos siguientes se usará la palabra **aplicación**.  
  
1.  Abra la página del Firewall de Windows. (En el cuadro de búsqueda del menú **Inicio** , escriba **Firewall de Windows**).  
  
2.  Haga clic en **Permitir una aplicación o una característica a través de Firewall de Windows**.  
  
3.  En la lista **Aplicaciones y características permitidas:** , busque **Detección del depurador remoto de Visual Studio**. Si aparece en la lista, asegúrese de que está seleccionada y de que también estén seleccionados uno o varios tipos de red.  
  
4.  Si no aparece **Detección del depurador remoto de Visual Studio** , haga clic en **Permitir otra aplicación**. Si aún no lo ve en el **agregar una aplicación** ventana, haga clic en **examinar** y vaya a  **\<directorio de instalación de Visual Studio > \Common7\IDE\Remote Debugger**. Busque la carpeta correspondiente de la aplicación (x86, x64, Appx) y, a continuación, seleccione **msvsmon.exe**. A continuación, haga clic en **Agregar**.  
  
5.  En el **permite aplicaciones y características** lista, seleccione **Visual Studio Remote Debugger**. Active uno o más tipos de red (**dominio, doméstica/de trabajo (privada) o pública**) para la comunicación con el monitor de depuración remota. Los tipos deben incluir la red a la que está conectado el equipo de Visual Studio. 

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-remote-computer"></a>Compruebe que los puertos estén abiertos en el Firewall de Windows en el equipo remoto  
 Los componentes de depuración remota pueden instalarse en el equipo remoto o ejecutarse desde un directorio compartido. El firewall del equipo remoto debe configurarse en ambos casos. Los componentes de depuración remota se encuentra en:  
  
 **\<Directorio de instalación de Visual Studio > \Common7\IDE\Remote Debugger**  
  
 Las instrucciones para configurar el firewall de Windows varían ligeramente en los distintos sistemas operativos. En Windows 8/8.1, Windows 10 y Windows Server 2012, la palabra **aplicación** se usa; en Windows 7 o Windows Server 2008, la palabra **programa** se usa;  En los pasos siguientes se usará la palabra **aplicación**.  
  
1.  Abra la página del Firewall de Windows. (En el cuadro de búsqueda del menú **Inicio** , escriba **Firewall de Windows**).  
  
2.  Haga clic en **Permitir una aplicación o una característica a través de Firewall de Windows**.  
  
3.  En el **permite aplicaciones y características** lista, busque **Visual Studio Remote Debugger**. Si aparece en la lista, asegúrese de que está seleccionada y de que también estén seleccionados uno o varios tipos de red.  
  
4.  Si **Visual Studio Remote Debugger** no es aparece, haga clic en **permitir otra aplicación**. Si aún no lo ve en el **agregar una ventana de aplicación**, haga clic en **examinar** y vaya a  **\<directorio de instalación de Visual Studio > \Common7\IDE\Remote Debugger**. Busque la carpeta correspondiente de la aplicación (x86, x64, Appx) y, a continuación, seleccione **msvsmon.exe**. A continuación, haga clic en **Agregar**.  
  
5.  En el **aplicaciones permitidas** lista, seleccione **Visual Studio Remote Debugger**. Active uno o más tipos de red (**dominio, doméstica/de trabajo (privada) o pública**) para la comunicación con el monitor de depuración remota. Los tipos deben incluir la red a la que está conectado el equipo de Visual Studio. 

### <a name="managed-or-native-compatibility-mode-open-additional-ports-on-the-remote-computer"></a>(Modo de compatibilidad administrado o nativo) Abrir puertos adicionales en el equipo remoto

Si se usa el modo de compatibilidad para que el depurador (**Herramientas > Opciones > depuración**), deben abrir puertos adicionales. Modo de compatibilidad permite a una versión heredada del depurador y diferentes puertos son necesarios.

> [!NOTE]
> La versión heredada del depurador es el depurador de Visual Studio 2010.
  
|||||  
|-|-|-|-|  
|**Puertos**|**Entrante/saliente**|**Protocolo**|**Descripción**|  
|135, 139, 445|Saliente|TCP|Requerido.|  
|137, 138|Saliente|UDP|Requerido.|  
|500, 4500|Saliente|UDP|Necesario si la directiva de dominio exige que la comunicación de red se realice a través de IPSec.|  
|80|Saliente|TCP|Necesario para la depuración en el servidor web.|
  
## <a name="see-also"></a>Vea también  
 [Depuración remota](../debugger/remote-debugging.md)