---
title: Solución de problemas de VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e740860046ee9d18a137dbd513202e259e90bf79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557976"
---
# <a name="troubleshooting-vspackages"></a>Solución de problemas de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A continuación se indican los problemas comunes que podría tener con el VSPackage y sugerencias para resolverlos.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Para solucionar problemas de un VSPackage que impide que se inicie Visual Studio  
  
- Inicie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en modo seguro.  
  
     Para iniciar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en modo seguro, en un símbolo del sistema, escriba **devenv.exe/SafeMode**.  
  
     Durante este proceso no se cargan VSPackages, excepto los VSPackages que se incluyen con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Para solucionar problemas de un VSPackage que no carga  
  
1. Asegúrese de que está usando la raíz del registro en la que se ha registrado el VSPackage para ejecutarse, normalmente la raíz experimental del registro.  
  
     Para obtener más información, vea [la instancia experimental](../extensibility/the-experimental-instance.md).  
  
2. Si el VSPackage está destinado a ejecutarse en la raíz del registro experimental, asegúrese de que está ejecutando la versión experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
     Para ejecutar la versión experimental, escriba lo siguiente en una ventana de comandos: **devenv/rootsuffix exp**.  
  
3. Compruebe las entradas del registro de VSPackage.  
  
     Para obtener más información, vea [registrar VSPackages](internals/registering-vspackages.md) y [administrar VSPackages](../extensibility/managing-vspackages.md).  
  
4. Abra la ventana de **salida** de la instancia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que no puede cargar el VSPackage. En esa ventana se puede mostrar información sobre por qué no se puede cargar el VSPackage.  
  
    > [!NOTE]
    > Si va a iniciar la versión experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] desde el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] entorno de desarrollo integrado (IDE), inspeccione la ventana de **salida** de ambas versiones.  
  
5. Examine el registro de actividad.  
  
     Para obtener más información, vea [Cómo: usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
6. Para obtener más información sobre las excepciones producidas por el IDE, haga clic en **excepciones** en el menú **depurar** para habilitar las excepciones. En el cuadro de diálogo **excepciones** , seleccione los tipos de excepciones sobre los que desea obtener más información.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Para solucionar problemas de un VSPackage que no se registra  
  
1. Asegúrese de que el ensamblado VSPackage reside en una ubicación de confianza. RegPkg no puede registrar ensamblados en una ubicación que no sea de confianza o de confianza parcial, como un recurso compartido de red en la configuración de seguridad predeterminada de .net. Aunque aparece una advertencia cada vez que un usuario crea un proyecto en una ubicación que no es de confianza, la casilla "no volver a mostrar este mensaje" puede impedir que se reproduzca esta advertencia.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Para solucionar problemas de un comando que no está visible o que genera un error al hacer clic en un comando  
  
1. Combine los comandos de menú nuevos o modificados y los ya existentes en el IDE; para ello, escriba lo siguiente en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] símbolo del sistema: **devenv/rootsuffix exp/Setup**.  
  
2. Asegúrese de que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] puede encontrar UI.dll para el VSPackage.  
  
    1. Busque el CLSID del VSPackage en la sección paquetes del registro:  
  
         HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \Packages  
  
    2. Compruebe que la ruta de acceso proporcionada por la subclave SatelliteDll es correcta.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Para solucionar problemas de un VSPackage que se comporta de forma inesperada  
  
1. Establezca puntos de interrupción en el código.  
  
     Los buenos puntos de partida para la depuración son el constructor y el método de inicialización. También puede establecer puntos de interrupción en el área que desea evaluar, como un comando de menú. Para habilitar los puntos de interrupción, debe ejecutar en el depurador.  
  
    1. En el menú **Proyecto** , haga clic en **Propiedades**.  
  
    2. En el cuadro de diálogo **páginas de propiedades** , seleccione la pestaña **depurar** .  
  
    3. En el cuadro argumentos de la **línea de comandos** , escriba el sufijo raíz del entorno de desarrollo al que se destina el VSPackage. Por ejemplo, para seleccionar la compilación experimental, escriba: **/RootSuffix exp**.  
  
    4. En el menú **depurar** , haga clic en **iniciar depuración** o presione F5.  
  
        > [!NOTE]
        > Si está depurando un proyecto, cree o cargue una instancia existente del proyecto ahora.  
  
2. Use el registro de actividad.  
  
     Seguimiento del comportamiento de VSPackage escribiendo información en el registro de actividad en los puntos clave. Esta técnica es especialmente útil cuando se ejecuta un VSPackage en un entorno comercial. Para obtener más información, vea [Cómo: usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
3. Use símbolos públicos.  
  
     Para mejorar la legibilidad durante la depuración, puede adjuntar símbolos al depurador.  
  
    1. En el menú **herramientas/opciones** , desplácese hasta el cuadro de diálogo **depuración/símbolos** .  
  
    2. Agregue esta **Ubicación de archivo de símbolos (. pdb)**:  
  
       `https://msdl.microsoft.com/download/symbols`  
  
    3. Para mejorar el rendimiento, especifique una carpeta de caché de símbolos, por ejemplo:  

       `C:\symbols`  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Para solucionar problemas de un VSPackage que falta o de una de sus dependencias  
  
1. En el caso de código administrado, asegúrese de que las rutas de acceso de referencia son correctas.  
  
   1. En el menú **Proyecto** , haga clic en **Propiedades**.  
  
   2. Seleccione la pestaña **referencias** en el cuadro de diálogo **páginas de propiedades** y asegúrese de que todas las rutas de acceso son correctas. Como alternativa, puede usar la **Examinador de objetos** para buscar los objetos a los que se hace referencia.  
  
        En el caso de código administrado, puede usar el [Fuslogvw.exe (visor de registro de enlaces de ensamblados)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) para mostrar los detalles de las cargas de ensamblado con errores.  
  
2. En el caso de código no administrado, busque el CLSID del VSPackage en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nodo del registro CLSID:  
  
    HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \CLSID  
  
   Asegúrese de que la entrada InprocServer32 tiene la ruta de acceso correcta del archivo dll de VSPackage.  
  
## <a name="see-also"></a>Consulte también  
 [VSPackages](../extensibility/internals/vspackages.md)
