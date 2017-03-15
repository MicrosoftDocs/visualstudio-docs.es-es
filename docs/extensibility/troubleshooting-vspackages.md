---
title: Solucionar problemas de VSPackages | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 933b0177e3287717b2cfb900996b947db7034ee5
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshooting-vspackages"></a>Solucionar problemas de VSPackages
Siguientes son problemas comunes que pueden surgir con el VSPackage y sugerencias para solucionar los problemas.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Solucionar problemas de un VSPackage que impide que Visual Studio a partir de  
  
-   Iniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en modo seguro.  
  
     Para iniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en modo seguro, en un símbolo del sistema, escriba **devenv.exe /safemode**.  
  
     Durante este proceso no se cargan VSPackages excepto los VSPackages que se incluyen con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Solucionar problemas de un VSPackage que no se carga  
  
1.  Asegúrese de que está utilizando la raíz del registro en el que está registrado el VSPackage para ejecutar, normalmente, la raíz del registro experimental.  
  
     Para obtener más información, consulte [la instancia Experimental](../extensibility/the-experimental-instance.md).  
  
2.  Si se destina el VSPackage para ejecutarse en la raíz del registro experimental, asegúrese de que está ejecutando la versión experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Para ejecutar la versión experimental, escriba lo siguiente en una ventana de comandos: **devenv /rootsuffix exp**.  
  
3.  Compruebe las entradas del registro de VSPackage.  
  
     Para obtener más información, consulte [registrar VSPackages](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd) y [administrar VSPackages](../extensibility/managing-vspackages.md).  
  
4.  Abra la **salida** ventana de la instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que no se puede cargar el VSPackage. Obtener información acerca de por qué no cargar el VSPackage puede mostrarse en la ventana.  
  
    > [!NOTE]
    >  Si va a iniciar la versión experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inspeccionar el entorno de desarrollo integrado (IDE), el **salida** ventana de ambas versiones.  
  
5.  Examine el registro de actividad.  
  
     Para obtener más información, consulte [Cómo: utilizar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
6.  Para obtener más información acerca de las excepciones producidas por el IDE, haga clic en **excepciones** en el **depurar** menú para habilitar las excepciones. En el **excepciones** cuadro de diálogo Seleccionar los tipos de excepciones que desee obtener más información.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Solucionar problemas de un VSPackage que no registra  
  
1.  Asegúrese de que el ensamblado de VSPackage reside en una ubicación de confianza. RegPkg no puede registrar los ensamblados en una ubicación de confianza o de confianza parcial, como un recurso compartido de red en la configuración de seguridad de .net de forma predeterminada. Aunque una advertencia aparece cuando un usuario crea un proyecto en una ubicación de confianza, la casilla de verificación "no mostrar este mensaje de nuevo" puede evitar esta advertencia no vuelva a producirse.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Solucionar problemas de un comando que no es visible o que genera un error al hacer clic en un comando  
  
1.  Combinar los comandos de menú nuevos o modificados y ya hay en el IDE, escriba lo siguiente en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] símbolo: **devenv /rootsuffix Exp/Setup**.  
  
2.  Asegúrese de que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede encontrar UI.dll para su VSPackage.  
  
    1.  Busque el CLSID del VSPackage en la sección de paquetes del registro:  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<versión >*\Packages  
  
    2.  Compruebe que la ruta de acceso dada por la subclave SatelliteDll es correcta.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Solucionar problemas de un VSPackage que se comporte de forma inesperada  
  
1.  Establezca puntos de interrupción en el código.  
  
     Buenos puntos de partida para la depuración son el constructor y el método de inicialización. También puede establecer puntos de interrupción en el área que va a evaluar como un comando de menú. Para habilitar los puntos de interrupción, debe ejecutar bajo el depurador.  
  
    1.  En el **proyecto** menú, haga clic en **propiedades**.  
  
    2.  En el **páginas de propiedades** cuadro de diálogo, seleccione la **depurar** ficha.  
  
    3.  En el **argumentos de línea de comandos** , escriba el sufijo de la raíz del entorno de desarrollo que los destinos de VSPackage. Por ejemplo, para seleccionar la compilación experimental, escriba: **RootSuffix Exp**.  
  
    4.  En el **depurar** menú, haga clic en **Iniciar depuración** o presione F5.  
  
        > [!NOTE]
        >  Si depura un proyecto, cree o cargue una instancia existente del proyecto ahora.  
  
2.  Utilice el registro de actividad.  
  
     Seguimiento VSPackage comportamiento escribiendo información en el registro de actividad en los puntos clave. Esta técnica es especialmente útil cuando se ejecuta un paquete VSPackage en un entorno minorista. Para obtener más información, consulte [Cómo: utilizar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Usar símbolos públicos.  
  
     Para mejorar la legibilidad durante la depuración, puede adjuntar símbolos al depurador.  
  
    1.  Desde el **herramientas/opciones** menú, navegue hasta la **y símbolos de depuración** cuadro de diálogo.  
  
    2.  Agregue esta **símbolos de la ubicación del archivo (.pdb)**:  
  
         [http://msdl.Microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Para mejorar el rendimiento, especifique una carpeta de caché de símbolos, por ejemplo:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Solucionar problemas de un VSPackage que faltan o una de sus dependencias  
  
1.  Para código administrado, asegúrese de que las rutas de acceso de referencia son correctos.  
  
    1.  En el **proyecto** menú, haga clic en **propiedades**.  
  
    2.  Seleccione el **referencias** ficha en el **páginas de propiedades** cuadro de diálogo y asegúrese de que todas las rutas de acceso son correctos. Como alternativa, puede utilizar el **Examinador de objetos** para buscar los objetos que se hace referencia.  
  
         Código administrado, puede utilizar el [Fuslogvw.exe (Visor de registro de enlaces de ensamblados)](http://msdn.microsoft.com/Library/e32fa443-0778-4cc3-bf36-5c8ea297d296) para mostrar los detalles de las cargas de ensamblado con errores.  
  
2.  Para código no administrado, buscar el CLSID del VSPackage en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nodo de registro CLSID:  
  
     HKLM\Software\Microsoft\Visual Studio\\*\<versión >*\CLSID  
  
 Asegúrese de que la entrada InprocServer32 tiene la ruta de acceso correcta del archivo dll de VSPackage.  
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)
