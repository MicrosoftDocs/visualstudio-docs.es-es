---
title: Solución de problemas de VSPackages ( Solución de problemas de VSPackages) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4827a36bd8e76462a137ae7e903c1ab624121c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698918"
---
# <a name="troubleshooting-vspackages"></a>Solución de problemas de VSPackages
A continuación se muestran los problemas comunes que puede tener con el VSPackage y sugerencias para resolver los problemas.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Para solucionar problemas de un VSPackage que impide que Visual Studio se inicie

- Comience [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en modo seguro.

   Para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] iniciar en modo seguro, en un símbolo del sistema, escriba **devenv.exe /safemode**.

   Durante este proceso no se carganingún VSPackages [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]excepto los VSPackages que se incluyen con .

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Para solucionar problemas de un VSPackage que no se carga

1. Asegúrese de que está utilizando la raíz del registro en la que el VSPackage está registrado para ejecutarse, normalmente la raíz del registro experimental.

    Para obtener más información, consulte [La instancia experimental](../extensibility/the-experimental-instance.md).

2. Si el VSPackage está destinado a ejecutarse en la raíz del registro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]experimental, asegúrese de que está ejecutando la versión experimental de .

    Para ejecutar la versión experimental, escriba lo siguiente en una ventana de comandos: **devenv /rootsuffix exp**.

3. Compruebe las entradas del registro de VSPackage.

    Para obtener más información, vea [Registrar VSPackages](registering-and-unregistering-vspackages.md) y [Administrar VSPackages](../extensibility/managing-vspackages.md).

4. Abra el **output** ventana [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de la instancia de que no se puede cargar el VSPackage. La información sobre por qué el VSPackage no se puede cargar se puede mostrar en esa ventana.

   > [!NOTE]
   > Si está iniciando la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versión experimental desde el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE), inspeccione la ventana **Salida** de ambas versiones.

5. Examine el registro de actividad.

    Para obtener más información, consulte [Cómo: Usar el registro](../extensibility/how-to-use-the-activity-log.md)de actividad .

6. Para obtener más información acerca de las excepciones producidas por el IDE, haga clic en **Excepciones** en **el** depurar menú para habilitar las excepciones. En el cuadro de diálogo **Excepciones,** seleccione los tipos de excepciones sobre los que desea obtener más información.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Para solucionar problemas de un VSPackage que no se registra

1. Asegúrese de que el ensamblado VSPackage reside en una ubicación de confianza. RegPkg no puede registrar ensamblados en una ubicación que no sea de confianza o que no sea de confianza parcial, como un recurso compartido de red en la configuración de seguridad predeterminada de .net. Aunque aparece una advertencia cada vez que un usuario crea un proyecto en una ubicación que no es de confianza, la casilla de verificación "no volver a mostrar este mensaje" puede impedir que se repita esta advertencia.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Para solucionar problemas de un comando que no está visible o que genera un error al hacer clic en un comando

1. Combine los comandos de menú nuevos o modificados y [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] los que ya están en el IDE escribiendo lo siguiente en el símbolo del sistema: **devenv /rootsuffix Exp /setup**.

2. Asegúrese [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de que puede encontrar UI.dll para el VSPackage.

   1. Busque el CLSID del VSPackage en la sección Packages del registro:

        HKLM, Software, Microsoft,\\Visual*\<Studio, versión>* paquetes

   2. Compruebe que la ruta de acceso proporcionada por la subclave SatelliteDll es correcta.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Para solucionar problemas de un VSPackage que se comporta inesperadamente

1. Establezca puntos de interrupción en el código.

     Los buenos puntos de partida para la depuración son el constructor y el método de inicialización. También puede establecer puntos de interrupción en el área que desea evaluar, como un comando de menú. Para habilitar los puntos de interrupción, debe ejecutarse en el depurador.

    1. En el menú **Proyecto** , haga clic en **Propiedades**.

    2. En el cuadro de diálogo Páginas de **propiedades,** seleccione la pestaña **Depurar.**

    3. En el argumentos de línea de **comandos** cuadro, escriba el sufijo raíz del entorno de desarrollo que los destinos de VSPackage. Por ejemplo, para seleccionar la compilación experimental, escriba: **/RootSuffix Exp**.

    4. En el menú **Depurar,** haga clic en **Iniciar depuración** o presione F5.

        > [!NOTE]
        > Si está depurando un proyecto, cree o cargue una instancia existente del proyecto ahora.

2. Utilice el registro de actividad.

     Seguimiento del comportamiento de VSPackage escribiendo información en el registro de actividad en puntos clave. Esta técnica es especialmente útil cuando se ejecuta un VSPackage en un entorno comercial. Para obtener más información, consulte [Cómo: Usar el registro](../extensibility/how-to-use-the-activity-log.md)de actividad .

3. Utilice símbolos públicos.

     Para mejorar la legibilidad durante la depuración, puede adjuntar símbolos al depurador.

    1. En el menú **Herramientas/Opciones,** vaya al cuadro de diálogo **Depuración/Símbolos.**

    2. Agregue esta ubicación del **archivo de símbolo (.pdb):**

         `https://msdl.microsoft.com/download/symbols`

    3. Para mejorar el rendimiento, especifique una carpeta de caché de símbolos, por ejemplo:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Para solucionar problemas de un VSPackage que falta o una de sus dependencias

1. Para el código administrado, asegúrese de que las rutas de acceso de referencia son correctas.

   1. En el menú **Proyecto** , haga clic en **Propiedades**.

   2. Seleccione la pestaña **Referencias** en el cuadro de diálogo **Páginas** de propiedades y asegúrese de que todas las rutas son correctas. Como alternativa, puede utilizar el **Examinador de objetos** para buscar los objetos a los que se hace referencia.

        Para el código administrado, puede usar [Fuslogvw.exe (Assembly Binding Log Viewer)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) para mostrar los detalles de las cargas de ensamblado con errores.

2. Para el código no administrado, busque el CLSID del VSPackage en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nodo del Registro CLSID:

    La\\*\<versión de *HKLM-Software-Microsoft-Visual Studio>de la versión de CLSID

   Asegúrese de que la entrada InprocServer32 tiene la ruta de acceso correcta del archivo dll de VSPackage.

## <a name="see-also"></a>Vea también
- [VSPackages](../extensibility/internals/vspackages.md)
