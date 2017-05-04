---
caps.handback.revision: 24
---
# Solucionar problemas de empaquetado e implementaci&#243;n de SharePoint
  En este tema se tratan diversos problemas que pueden producirse al empaquetar e implementar soluciones de SharePoint.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## Habilitar la depuración mejorada  
 Si desea realizar un diagnóstico entre Visual Studio, SharePoint y otras capas, puede usar la clave del Registro EnableDiagnostics para ver el seguimiento de la pila.  Para obtener más información, vea [Depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## Agregar la salida del proyecto al paquete de solución  
 Puede agregar la salida del proyecto a un paquete a través del Diseñador de paquetes.  Sin embargo, cuando agregue la salida del proyecto, asegúrese de que la plataforma del proyecto coincide con la plataforma de la solución de SharePoint.  Le recomendamos que use el destino de plataforma **Any CPU** en los ensamblados que desee implementar en un servidor de SharePoint.  Para obtener más información, vea [Página Compilación, Diseñador de proyectos &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md) y [Configuración de compilador avanzada &#40;Cuadro de diálogo, Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  
  
## Errores y advertencias de validación  
 Las herramientas de desarrollo de SharePoint de Visual Studio realizan pasos de validación para comprobar que el paquete de solución se crea de forma correcta.  También puede crear pasos de validación personalizados para sus características y paquetes.  Para obtener más información, vea [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## Resolución de conflictos de implementación  
 Al implementar una solución de SharePoint, pueden producirse colisiones cuando un elemento del servidor tiene el mismo nombre, dirección URL o identificador que un elemento del paquete de solución.  Puede cambiar la propiedad **Deployment Conflict Resolution** para resolver, notificar u omitir las colisiones de los módulos, elementos web, instancias de lista y tipos de contenido.  
  
 En la tabla siguiente se muestran los valores de la propiedad **Deployment Conflict Resolution**.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|Automatic|Detecta las colisiones y resuelve los conflictos automáticamente.|  
|Prompt|Detecta las colisiones y las notifica al desarrollador de software antes de resolver los conflictos.|  
|None|No detecta las colisiones.|  
  
## Diferencias entre la implementación y F5  
 Cuando se usa [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para implementar un proyecto de SharePoint en el servidor de SharePoint local para su comprobación y depuración, hay algunos pasos adicionales que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] realiza.  
  
1.  Restablece Internet Información Services \(IIS\) durante el paso de implementación.  
  
2.  Asocia automáticamente los flujos de trabajo.  
  
3.  Establece el orden de activación de características según la jerarquía del Diseñador de paquetes.  
  
 Puede agregar pasos de implementación personalizados para cambiar el comportamiento de F5.  Para obtener más información, vea [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## Retrasar la aparición de la página de SharePoint al implementar un elemento web visual  
 La página de SharePoint tarda mucho en aparecer cuando se implementa un elemento web visual en la carpeta Bin de [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] o [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)].  Si se cambian los archivos de un directorio de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] de nivel superior, como el directorio Bin, se volverá a compilar toda la aplicación web.  Esto puede generar un retraso de hasta 25 segundos en la presentación de la página de SharePoint.  
  
### Mensaje de error  
 Ninguno.  
  
### Resolución  
 Para evitar este problema, siga estos pasos:  
  
1.  Instale la actualización KB967535 que se describe en el artículo de Soporte técnico de Microsoft [REVISIÓN: existe una revisión disponible para solucionar dos problemas de ASP.NET en IIS 7.0 para Windows Vista y Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055).  
  
2.  Agregue la línea siguiente al archivo Web.config.  
  
    ```  
    <compilation batch="false" optimizeCompilations="true">  
    ```  
  
## Al implementar del proyecto de SharePoint se produce el siguiente error: "Error al extraer el archivo cab de la solución"  
 Si el nombre de algún elemento de proyecto de SharePoint contiene paréntesis, se produce un error en la implementación de la solución.  
  
### Mensaje de error  
 En el paso 'Agregar solución' de la implementación se ha producido el siguiente error: "Error al extraer el archivo cab de la solución".  
  
### Resolución  
 Para evitar este problema, quite los paréntesis de los nombres de elementos de proyecto de SharePoint.  
  
## Aparece un error al implementar un elemento web visual en un sitio de una aplicación web diferente  
 La primera vez que implementa un elemento web visual en un sitio de otra aplicación web distinta de la que está implementando en la actualidad \(mediante la modificación de la propiedad SiteUrl del elemento web visual\), se produce un error.  
  
### Mensaje de error  
 En el paso 'Agregar solución' de la implementación se produce el siguiente error: "Ya se ha instalado una característica con Id. \[\#\] en este conjunto de servidores.  Use el atributo fuerza para volver a agregar la característica de modo explícito".  
  
### Resolución  
 Este error se produce debido al modo en que se retractan las características de elementos web visuales en SharePoint.  Para implementar el elemento web visual correctamente, implemente de nuevo la solución. Para ello, presione la tecla F5.  
  
## Aparece una advertencia al implementar controles de usuario anidados  
 Esta advertencia se produce al implementar una solución de SharePoint que contiene controles de usuario anidados, como un elemento web visual que incluye un control de usuario o un control de usuario que incluye un elemento web visual u otro control de usuario.  Esta advertencia se produce si agrega un control a un diseñador arrastrándolo desde el cuadro de herramientas o mediante la directiva @Register en la vista Código fuente.  
  
### Mensaje de error  
 Advertencia 1 El elemento '\[*Control Name*\]' es desconocido.  Esto se puede producir si hay un error de compilación en el sitio web o no se encuentra el archivo web.config.  
  
### Resolución  
 Si el sistema de proyectos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no reconoce un control de usuario anidado, no puede proporcionar Intellisense y emite la advertencia.  El sistema de proyectos no reconoce un control de usuario anidado si no se ha compilado el proyecto y el diseñador no se ha cerrado y se ha vuelto a abrir, o si está habilitada la opción de retracción automática, que hace que el control de usuario se retire del subárbol de SharePoint después de la depuración.  
  
 Para quitar esta advertencia, compile el proyecto y, a continuación, cierre el diseñador y vuelva a abrirlo, o deshabilite la opción de retracción automática en el proyecto.  Para ello, desactive la casilla **Retraer automáticamente después de depurar** en la pestaña **SharePoint** del cuadro de diálogo Propiedades del proyecto.  
  
## Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  