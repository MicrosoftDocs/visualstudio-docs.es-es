---
title: Solucionar problemas de VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d89c3181757a0ed95b818ba2e73197511bf06e4d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434249"
---
# <a name="troubleshooting-vspackages"></a>Solución de problemas de VSPackages
Estos son los problemas comunes que podría tener con el paquete de VS y sugerencias para solucionar los problemas.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Para solucionar problemas de un VSPackage que impide que Visual Studio iniciando

- Iniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en modo seguro.

   Para iniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en modo seguro, en un símbolo del sistema, escriba **devenv.exe /safemode**.

   Durante este proceso no se cargan VSPackages, excepto los VSPackages que se incluyen con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Para solucionar problemas de un VSPackage que no se carga

1. Asegúrese de que está usando la raíz del registro en el que se registra el VSPackage para ejecutar, normalmente la raíz del registro experimental.

    Para obtener más información, consulte [la instancia Experimental](../extensibility/the-experimental-instance.md).

2. Si se destina el VSPackage para ejecutarse en la raíz del registro experimental, asegúrese de que se está ejecutando la versión experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

    Para ejecutar la versión experimental, escriba lo siguiente en una ventana de comandos: **devenv /rootsuffix exp**.

3. Compruebe las entradas del registro de VSPackage.

    Para obtener más información, consulte [registrar VSPackages](registering-and-unregistering-vspackages.md) y [administrar VSPackages](../extensibility/managing-vspackages.md).

4. Abra el **salida** ventana de la instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que no se puede cargar el VSPackage. Información sobre por qué se puede cargar el VSPackage puede mostrarse en esa ventana.

   > [!NOTE]
   > Si va a iniciar la versión experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE), inspeccione la **salida** ventana de ambas versiones.

5. Examine el registro de actividad.

    Para obtener más información, vea [Cómo: Usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).

6. Para obtener más información acerca de las excepciones producidas por el IDE, haga clic en **excepciones** en el **depurar** menú para habilitar las excepciones. En el **excepciones** cuadro de diálogo Seleccionar los tipos de excepciones sobre la que desea obtener más información.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Para solucionar problemas de un VSPackage que no registra

1. Asegúrese de que el ensamblado de VSPackage reside en una ubicación de confianza. RegPkg no puede registrar los ensamblados en una ubicación de confianza o de confianza parcial, como un recurso compartido de red en la configuración de seguridad de .net de forma predeterminada. Aunque aparece una advertencia cada vez que un usuario crea un proyecto en una ubicación de confianza, la casilla "no mostrar este mensaje de nuevo" puede evitar esta advertencia no vuelva a producirse.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Para solucionar problemas de un comando que no está visible o que genera un error al hacer clic en un comando

1. Combinar los comandos de menú nuevos o modificados y los que ya se encuentran en el IDE escribiendo lo siguiente en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] símbolo del sistema: **devenv /rootsuffix Exp/Setup**.

2. Asegúrese de que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] encontrará UI.dll para el VSPackage.

   1. Buscar el CLSID del VSPackage en la sección de paquetes del registro:

        HKLM\Software\Microsoft\Visual Studio\\*\<version>* \Packages

   2. Compruebe que la ruta de acceso proporcionado por la subclave SatelliteDll es correcta.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Para solucionar problemas de un VSPackage que se comporta de forma inesperada

1. Establezca puntos de interrupción en el código.

     Buenos puntos de partida para la depuración son el constructor y el método de inicialización. También puede establecer puntos de interrupción en el área que va a evaluar como un comando de menú. Para habilitar los puntos de interrupción, debe ejecutar en el depurador.

    1. En el menú **Proyecto**, haga clic en **Propiedades**.

    2. En el **páginas de propiedades** cuadro de diálogo, seleccione el **depurar** ficha.

    3. En el **argumentos de línea de comandos** , escriba el sufijo de la raíz del entorno de desarrollo que los destinos de VSPackage. Por ejemplo, para seleccionar la compilación experimental, escriba: **RootSuffix Exp**.

    4. En el **depurar** menú, haga clic en **Iniciar depuración** o presione F5.

        > [!NOTE]
        > Si está depurando un proyecto, cree o cargue una instancia existente del proyecto ahora.

2. Utilice el registro de actividad.

     Seguimiento VSPackage comportamiento escribiendo información en el registro de actividad en los puntos clave. Esta técnica es especialmente útil cuando se ejecuta un paquete VSPackage en un entorno minorista. Para obtener más información, vea [Cómo: Usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).

3. Usar símbolos públicos.

     Para mejorar la legibilidad durante la depuración, puede adjuntar los símbolos para el depurador.

    1. Desde el **herramientas/opciones** menú, vaya a la **depuración/símbolos** cuadro de diálogo.

    2. Agregar esto **ubicación del archivo (.pdb) de símbolos**:

         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)

    3. Para mejorar el rendimiento, especifique una carpeta de caché de símbolos, por ejemplo:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Para solucionar problemas de un VSPackage que faltan o uno de sus dependencias

1. Para código administrado, asegúrese de que las rutas de acceso de referencia son correctos.

   1. En el menú **Proyecto**, haga clic en **Propiedades**.

   2. Seleccione el **referencias** pestaña en el **páginas de propiedades** cuadro de diálogo y asegúrese de que todas las rutas de acceso son correctos. Como alternativa, puede usar el **Examinador de objetos** para buscar los objetos que se hace referencia.

        Para código administrado, puede usar el [Fuslogvw.exe (Visor de registro de enlaces de ensamblados)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) para mostrar los detalles de las cargas de ensamblado con error.

2. Para código no administrado, busque el CLSID del VSPackage en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nodo de registro CLSID:

    HKLM\Software\Microsoft\Visual Studio\\*\<version>* \CLSID

   Asegúrese de que la entrada InprocServer32 tiene la ruta de acceso correcta del archivo dll de VSPackage.

## <a name="see-also"></a>Vea también
- [VSPackages](../extensibility/internals/vspackages.md)