---
title: "Analizador de extensi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, analizador de errores de carga"
ms.assetid: 8d2bcc4e-9feb-45a5-8d8e-470346f0d39e
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Analizador de extensi&#243;n
El **Analizador de extensión** captura y registra los errores de carga de extensiones más habituales. El **Analizador de extensión** se ejecuta en su propia ventana de herramienta. El analizador informa de la causa de un error y muestra sugerencias sobre cómo corregirlo.  
  
 El [Analizador de extensión](http://go.microsoft.com/fwlink/?LinkId=205840) se puede descargar en la Galería de Visual Studio. Los ensamblados del **Analizador de extensión** se instalan en \<*Ruta de instalación de Visual Studio*\>\\Common7\\IDE\\PrivateAssemblies\\.  
  
## Explorador  
 Una vez instalado el **Analizador de extensión**, en el menú **Herramientas**, haga clic en **Analizador de extensión** y en **Explorador**. Se abrirá una ventana en la que se mostrarán todas las extensiones registradas en el equipo. Hay diferentes pestañas para los archivos VSIX, los VSPackages, los archivos PkgDef y los componentes MEF. Puede ordenar las listas por cualquiera de los nombres de columna.  
  
1.  En la pestaña VSIX se muestra información sobre las extensiones VSIX instaladas. Puede incluir componentes del sistema activando la casilla **Mostrar componentes del sistema**. En esta pestaña puede navegar a las entradas de registro de VSIX, abrir el manifiesto de VSIX en el editor XML de Visual Studio y abrir la carpeta en la que se ha instalado la extensión VSIX.  
  
2.  En la pestaña VSPackages se muestra información sobre los VSPackages que Visual Studio conoce, tanto si están cargados como si no lo están. También se especifica el identificador VSIX, el archivo .pkgdef y el GUID del VSPackage. Puede incluir VSPackages del sistema activando la casilla **Mostrar paquetes del sistema**. En esta pestaña puede navegar a las entradas de registro, ver la extensión VSIX que aparece en la pestaña VSIX, consultar el archivo .pkgdef en la pestaña Archivos PkgDef y analizar el VSPackage. Los resultados del análisis aparecen en el panel **Salida**.  
  
3.  En la pestaña Archivos PkgDef se muestra información sobre los archivos .pkgdef de las extensiones que Visual Studio conoce. Esta información incluye el identificador VSIX y la ruta de acceso de la extensión. Puede ir al registro o a la pestaña VSIX y consultar el archivo .pkgdef en el editor.  
  
4.  En la pestaña Componentes MEF se muestra información sobre los componentes MEF que Visual Studio conoce. Esta información incluye el identificador VSIX y la ruta de acceso en la que está instalada la extensión. Puede incluir componentes del sistema activando la casilla **Mostrar componentes del sistema**. También puede ir a la entrada VSIX correspondiente, al archivo .pkgdef y a la ubicación en la que se ha instalado la extensión.  
  
> [!WARNING]
>  Es posible que reciba un mensaje pidiéndole que active el registro de fusión. Para ello, seleccione una ubicación para los archivos de registro. Puede que se le pida que reinicie todas las instancias de Visual Studio para poder continuar.  
  
## Visor de registros  
 Puede ver los mensajes de registro con el **Visor de registros de extensión** si está ejecutando un proyecto que tiene activado el registro \(agregando \/log a los argumentos de la línea de comandos del proyecto\). Para obtener más información, consulta [\/Log](../ide/reference/log-devenv-exe.md). En la ventana **Visor de registros de extensión** se muestra la fecha, el agente de escucha, el tipo de entrada \(tipo de mensaje\), el tipo de error, información de clase o de interfaz y el mensaje del registro. Puede ordenar y filtrar la información.  
  
## Problemas comunes en la carga de extensiones  
 A continuación aparecen algunas de las causas habituales de los errores de carga de una extensión en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Problemas de dependencia. Se ha implementado una extensión de tal manera que no se encuentran los ensamblados dependientes.  
  
-   Excepciones. Al cargar un VSPackage, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] llama a su método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>. Si este método genera una excepción, se producirá un error en la carga del VSPackage. La mejor forma de aislar este problema consiste en recorrer el código SetSite.  
  
-   Registro incorrecto. Compruebe que la extensión esté firmada correctamente y que el VSPackage esté registrado usando la clave pública correcta.  
  
## Vea también  
 [Administración de VSPackages](../extensibility/managing-vspackages.md)