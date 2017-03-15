---
title: "Procedimientos recomendados de la p&#225;gina de inicio | Microsoft Docs"
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
  - "sugerencias de la página de inicio"
  - "procedimientos recomendados de la página de inicio"
  - "diseño de la página de inicio"
ms.assetid: f6ce1ce0-746e-4004-a37f-6f176f6f5851
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Procedimientos recomendados de la p&#225;gina de inicio
Dado que la página de inicio puede acceder a los comandos de Visual Studio y siempre se abre cuando se carga Visual Studio, se recomienda garantizar la estabilidad de cualquier página de inicio personalizada antes de usarla o distribuirla. En este tema se sugieren los procedimientos recomendados para un diseño sólido de la página de inicio y se incluyen instrucciones sobre cómo crear una interfaz de usuario \(UI\) útil.  
  
## Directrices de estabilidad  
  
### Disponibilidad de los recursos  
 La consideración más importante a la hora de crear una página de inicio personalizada sólida es garantizar la disponibilidad de todos los recursos necesarios:  
  
-   Todos los paquetes necesarios están instalados.  
  
-   Los paquetes están previamente cargados.  
  
-   Todos los ensamblados necesarios están en la carpeta \\PrivateAssemblies\\.  
  
-   Cada componente que usa una conexión de Internet o de red tiene rutas de acceso alternativas para los escenarios sin conexión y las conexiones interrumpidas.  
  
### Rendimiento  
 Si la página de inicio tiene grandes requisitos de memoria o carga muchos recursos, tenga en cuenta cómo puede verse afectado el rendimiento de inicio. Programe estas páginas de inicio para que carguen componentes a petición o en segundo plano, si es posible, de modo que el tiempo de inicio no aumente significativamente.  
  
### Proceso de desarrollo  
 Si modifica la página de inicio activa directamente, podría incluir errores sin querer, con el consecuente bloqueo de Visual Studio. Dado que la página de inicio se abre cada vez que se abre Visual Studio, es difícil corregir una página de inicio que se bloquea. Por lo tanto, se recomienda modificar las copias de los archivos de la página de inicio y probarlas en una instancia experimental de Visual Studio con fines de confiabilidad. Cuando la nueva página de inicio sea estable, puede establecerla para que se ejecute en la instancia principal de Visual Studio.  
  
> [!NOTE]
>  También se recomienda que pruebe cualquier página de inicio de terceros en una instancia experimental de Visual Studio antes de usarla en la instancia principal.  
  
##### Para probar una página de inicio en una instancia experimental de Visual Studio  
  
1.  Si usa la plantilla de proyecto de la página de inicio, presione F5. De lo contrario:  
  
    1.  Copie el archivo .xaml y cualquier texto o marcado complementario en \\%USERPROFILE%\\Mis documentos\\Visual Studio *\<versión\>*\\StartPages\\.  
  
    2.  Copie los ensamblados necesarios en *\<ruta de instalación de Visual Studio\>*\\Common7\\IDE\\PrivateAssemblies\\.  
  
    3.  Abra una instancia experimental de Visual Studio mediante el comando siguiente en un símbolo del sistema de Visual Studio.  
  
         **Devenv \/rootsuffix exp**  
  
2.  En el menú **Herramientas**, haga clic en **Opciones**. Seleccione **Entorno** y, luego, **Inicio**. En la lista **Personalizar página principal** seleccione el archivo StartPage.xaml cuyo nombre ha cambiado y, después, haga clic en **Aceptar**.  
  
3.  En el menú **Ver**, haga clic en **Página de inicio**.  
  
     Se abre la página de inicio personalizada. Si la página de inicio que está modificando se bloquea, puede reiniciar la instancia principal de Visual Studio, realizar las correcciones necesarias y, después, abrir otra instancia experimental para poder continuar modificando la página de inicio personalizada.  
  
 Si la página de inicio bloquea la instancia principal de Visual Studio, puede deshabilitar temporalmente las páginas de inicio personalizadas estableciendo el valor del Registro de HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\StartPage\\Default\\CustomizationEnabled en 0. Como alternativa, puede cambiar temporalmente el nombre del archivo .xaml de su página de inicio predeterminada actual. Cualquier medida le permitirá abrir Visual Studio el tiempo suficiente para solucionar el error.  
  
### Depuración  
 La ventana de herramientas de la página de inicio captura excepciones cuando se carga por primera vez una página de inicio, pero no detecta excepciones posteriormente. Puede indicar a Visual Studio que muestre todas las excepciones no controladas. Para ello, establezca el valor de Registro siguiente en "1".  
  
 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\General\\EnableUnhandledExceptionDisplay  
  
 La información de la excepción se mostrará en un cuadro de mensaje, lo que permite depurar controles en una página de inicio o en otras ubicaciones no controladas, incluso en la instancia principal de Visual Studio. Si no puede realizar la depuración después de producirse la excepción, puede reiniciar Visual Studio con el comando "devenv \/safemode", volver a la página de inicio anterior y, después, continuar con la depuración en la instancia experimental.  
  
### Rutas de acceso relativas  
 Al hacer referencia a rutas de acceso de archivo desde una página de inicio, use siempre una ruta de acceso relativa para permitir distintas configuraciones del sistema. Sin embargo, la raíz de todas las rutas de acceso relativas en una página de inicio no se resuelve en la carpeta \\StartPages\\ sino en la ..\\*Carpeta de instalación de Visual Studio*\\Common7\\IDE, que es donde se encuentra el archivo devenv.exe. Para establecer una ruta de acceso relativa a la carpeta \\StartPages\\, use el convertidor relativo de la página de inicio de Visual Studio. Para ello, establezca la propiedad `Source` del objeto en `vs:StartPageRelative`, como se muestra en el ejemplo siguiente.  
  
 XAML  
  
```  
<Image Source="{vs:StartPageRelative myImage.png}" .../>  
```  
  
 Use la sintaxis estándar de la ruta de acceso relativa al acceder a los recursos incluidos con Visual Studio o los archivos incluidos en otros paquetes.  
  
### Implementación  
 Las siguientes prácticas recomendadas son aplicables a la implementación de una página de inicio personalizada para otros usuarios.  
  
#### Configuración del usuario  
  
-   Respete la configuración del usuario. No sobrescriba las preferencias actuales de la página de inicio.  
  
#### VSIX  
 Estas prácticas se aplican a la implementación de VSIX:  
  
-   Use el elemento [GettingStartedGuide](http://msdn.microsoft.com/es-es/261bb1fd-abae-4ed6-80a8-90d5fc3bb8c6) en el manifiesto VSIX para señalar instrucciones sobre cómo establecer la página de inicio predeterminada.  
  
-   Use el elemento [Name](http://msdn.microsoft.com/es-es/d99d38d1-060b-401a-9b9f-ede2c6213a11) y el elemento [Description](http://msdn.microsoft.com/es-es/24ddc57e-e991-4a43-b0c9-0e76da293e99) del manifiesto VSIX para identificar claramente la extensión como una página de inicio y describir su finalidad.  
  
-   Compruebe que el manifiesto VSIX no contiene rutas de acceso absolutas.  
  
-   Al cargar el sitio web de la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847), , incluya el etiquetado pertinente para que los usuarios puedan identificar la extensión como una página de inicio.  
  
#### MSI  
 Si está produciendo una página de inicio como parte de una extensión mayor que está implementando en un paquete de Windows Installer \(MSI\), puede establecer la página de inicio como la página de inicio predeterminada del equipo de destino. Para lograrlo, escriba el nombre del archivo .xaml de la página de inicio en el valor de Uri de esta clave de Registro: HKCU\\Software\\Microsoft\\VisualStudio\\14.0\\StartPage\\Default\\. Use las siguientes directrices cuando establezca este valor de Registro:  
  
-   En el instalador, proporcione la interfaz de usuario para permitir que el usuario seleccione si se debe establecer la nueva página de inicio como predeterminada.  
  
-   Si el usuario desinstala la extensión, restaure el valor de Registro anterior.  
  
### Windows Presentation Framework \(WPF\)  
 El marcado XAML debe seguir los procedimientos recomendados de WPF. Para obtener información acerca de los procedimientos recomendados de [!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)] y [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] para el desarrollo de aplicaciones, vea los temas siguientes, según corresponda.  
  
|Área|Tema|  
|----------|----------|  
|Accesibilidad|[Accessibility Best Practices](../Topic/Accessibility%20Best%20Practices.md)|  
|Localización|[Información general sobre la globalización y la localización de WPF](../Topic/WPF%20Globalization%20and%20Localization%20Overview.md)|  
|Rendimiento|[Optimizar WPF: Rendimiento de aplicaciones](../Topic/Optimizing%20WPF%20Application%20Performance.md)|  
|Seguridad|[Seguridad \(WPF\)](../Topic/Security%20\(WPF\).md)|  
  
## Directrices de interfaz de usuario  
 Para garantizar una experiencia de usuario práctica e intuitiva con la página de inicio, use las siguientes directrices de la interfaz de usuario según corresponda.  
  
### Fila superior  
  
#### Titular  
  
-   Iguale el alto de la imagen de titular al alto de la definición de la fila que la contiene.  
  
-   Para adaptarse a distintos tamaños de ventana y resoluciones de pantalla, haga que la imagen de titular sea visualmente atractiva con cualquier ancho.  
  
-   Mantenga el área del titular despejada. No superponga el logotipo con botones o gráficos adicionales.  
  
### Columna izquierda  
  
#### Área del botón  
  
-   Coloque solo los controles que se usan con más frecuencia en el área del botón para que quede espacio para los nombres de los proyectos recientes que se van a mostrar. Se recomienda usar menos de cinco botones.  
  
#### Proyectos recientes  
  
-   Este control permite al usuario acceder a los proyectos recientes. Puede establecer el número de proyectos que deben mostrarse de 0 a 24. Dado que esta es la sección que se usa con más frecuencia de la página de inicio, se recomienda no quitarla.  
  
#### Opciones de la página de inicio  
  
-   Asegúrese de que las opciones **Cerrar la página después de cargar el proyecto** y **Mostrar la página al inicio** aparecen en la página de inicio.  
  
-   Para los controles adicionales en esta área, se recomienda usar las casillas o los botones de radio y asegurarse de que los controles se corresponden con las preferencias de la página de inicio.  
  
### Área de contenido  
  
#### Pestañas de nivel superior  
  
-   Evite agregar tantas pestañas que el control de pestaña se ajuste con los anchos de pantalla típicos.  
  
-   Use nombres descriptivos cortos para las pestañas.  
  
-   Asegúrese de que las pestañas representen áreas de contenido agrupadas.  
  
#### Pestañas de subnivel  
  
-   Use solo la navegación de subnivel si tiene más de dos subtemas.  
  
-   Evite agregar tantas pestañas que el control de pestaña se ajuste con los anchos de pantalla típicos.  
  
-   Use nombres descriptivos cortos para las pestañas.  
  
#### Contenido de las pestañas de subnivel  
  
-   Muestre un máximo de cinco elementos de contenido en una pestaña de subnivel.  
  
#### Contenido del elemento  
  
-   Muestre un máximo de cuatro vínculos por cada elemento de contenido.  
  
-   Si asocia imágenes con elementos de contenido, asegúrese de que cada imagen sea de 175 por 125 píxeles.  
  
-   Use títulos descriptivos cortos para los elementos de contenido.  
  
-   Limite las descripciones de los elementos de contenido a dos frases o menos.  
  
### General  
  
#### Animaciones  
  
-   Si usa animaciones, limítelas a 0,5 segundos o menos para evitar cualquier percepción de rendimiento incorrecto.  
  
#### Colores del entorno  
  
-   Respete la configuración del sistema para fuentes y colores.  
  
-   Use fondos claros.  
  
-   Use la detección de escritorio remoto para garantizar una degradación de color correcta en las sesiones remotas.  
  
## Vea también  
 [Arquitectura de la página de inicio](../misc/start-page-architecture.md)   
 [Implementar páginas de inicio personalizado](../extensibility/deploying-custom-start-pages.md)   
 [Agregar comandos de Visual Studio a una página de inicio](../extensibility/adding-visual-studio-commands-to-a-start-page.md)