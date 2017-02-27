---
title: "Implementar componentes COM con ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, componentes COM"
  - "componentes COM, implementar"
  - "componentes, implementar"
  - "implementar aplicaciones [ClickOnce], componentes COM"
  - "implementación COM sin registro"
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Implementar componentes COM con ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La implementación de componentes COM heredados ha sido normalmente una tarea difícil.  Es necesario que los componentes se registren globalmente, por lo que pueden producir efectos secundarios no deseados entre aplicaciones superpuestas.  Por lo general, esta situación no es problemática en aplicaciones de .NET Framework porque los componentes están completamente aislados de las aplicaciones o son compatibles en paralelo.  Visual Studio permite implementar componentes COM aislados en el sistema operativo Windows XP o posterior.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] proporciona un mecanismo fácil y seguro para implementar aplicaciones .NET.  Sin embargo, si sus aplicaciones utilizan componentes COM heredados, será necesario que realice pasos adicionales para implementarlos.  En este tema se describe cómo implementar componentes COM aislados y hacer referencia a los componentes nativos \(por ejemplo, de Visual Basic 6.0 o Visual C\+\+\).  
  
 Para obtener más información sobre cómo implementar componentes COM aislados, vea "Simplify App Deployment with [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] and Registration\-Free COM" en [http:\/\/msdn.microsoft.com\/msdnmag\/issues\/05\/04\/RegFreeCOM\/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).  
  
## COM sin registro  
 COM sin registro es una nueva tecnología para implementar y activar componentes COM aislados.  Funciona colocando toda la información del Registro y de la biblioteca de tipos del componente que normalmente se instala en el Registro del sistema en un archivo XML, denominado manifiesto, que se almacena en la misma carpeta que la aplicación.  
  
 Aislar un componente COM requiere que esté registrado en el equipo del desarrollador, pero no es necesario que esté registrado en el equipo del usuario final.  Para aislar un componente COM, lo único que debe hacer es establecer la propiedad **Aislada** de su referencia en **True**.  De forma predeterminada, esta propiedad se establece en **False**, lo que indica que se debería tratar como una referencia COM registrada.  Si esta propiedad tiene el valor **True**, hace que se cree un manifiesto para este componente en tiempo de compilación.  También hace que durante la instalación, se copien los archivos correspondientes en la carpeta de la aplicación.  
  
 Cuando el generador del manifiesto encuentra una referencia COM aislada, enumera todas las entradas de la clase `CoClass` de la biblioteca de tipos del componente, haciendo coincidir cada entrada con sus datos de registro correspondientes y generando definiciones de manifiesto para todas las clases COM del archivo de biblioteca de tipos.  
  
## Implementar componentes COM sin registro utilizando ClickOnce  
 La tecnología de implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es adecuada para implementar componentes COM aislados, ya que tanto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] como COM sin registro requieren que los componentes posean un manifiesto para ser implementados.  
  
 Normalmente, el autor del componente debe proporcionar un manifiesto.  Sin embargo, si no lo hace, Visual Studio es capaz de generar un manifiesto automáticamente para un componente COM.  La generación del manifiesto se realiza durante el proceso de publicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]; para obtener más información, vea [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md).  Esta característica también permite aprovechar componentes heredados creados en entornos de desarrollo anteriores, como Visual Basic 6.0.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementa los componentes COM de dos maneras:  
  
-   Utilice el arranque para implementar los componentes COM; esto funciona en todas las plataformas compatibles.  
  
-   Utilice la implementación de aislamiento de componentes nativos \(también conocida como COM sin registro\).  Sin embargo, esto sólo funcionará en un sistema operativo Windows XP o posterior.  
  
### Ejemplo de aislamiento e implementación de un componente COM sencillo  
 Para mostrar la implementación de componentes COM sin registro, en este ejemplo se crea en Visual Basic una aplicación basada en Windows que hace referencia a un componente COM nativo aislado creado en Visual Basic 6.0, y se implementa mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 En primer lugar, es necesario crear el componente COM nativo:  
  
##### Para crear un componente COM nativo  
  
1.  Utilizando Visual Basic 6.0, en el menú **Archivo**, haga clic en **Nuevo** y, a continuación, en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, seleccione el nodo **Visual Basic** y seleccione un proyecto **Archivo DLL de ActiveX**.  En el cuadro **Nombre**, escriba `VB6Hello`.  
  
    > [!NOTE]
    >  Con el sistema COM sin registro sólo se admiten los tipos de proyecto Archivo DLL de ActiveX y Control ActiveX; no se admiten los tipos de proyecto EXE de ActiveX ni documento ActiveX.  
  
3.  En el **Explorador de soluciones**, haga doble clic en **Class1.vb** para abrir el editor de texto.  
  
4.  En Class1.vb, agregue el código siguiente después del código generado para el método `New`:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Compile el componente.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
> [!NOTE]
>  El sistema COM sin registro sólo admite los tipos de proyecto de archivos DLL y COM.  Con el sistema COM sin registro no se pueden utilizar archivos EXE.  
  
 Ahora puede crear una aplicación basada en Windows y agregarle una referencia al componente COM.  
  
##### Para crear una aplicación basada en Windows mediante un componente COM  
  
1.  Utilizando Visual Basic, en el menú **Archivo**, haga clic en **Nuevo** y, a continuación, en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, seleccione el nodo **Visual Basic** y elija **Aplicación para Windows**.  En el cuadro **Nombre**, escriba `RegFreeComDemo`.  
  
3.  En el **Explorador de soluciones**, haga clic en el botón **Mostrar todos los archivos** para mostrar las referencias del proyecto.  
  
4.  Haga clic con el botón secundario del mouse en el nodo **Referencias** y seleccione **Agregar referencia** en el menú de acceso directo.  
  
5.  En el cuadro de diálogo **Agregar referencia**, haga clic en la ficha **Examinar**, navegue a VB6Hello.dll y selecciónela.  
  
     En la lista de referencias aparece **VB6Hello**.  
  
6.  Coloque el puntero en el **Cuadro de herramientas**, seleccione un control **Button** y arrástrelo hasta el formulario **Form1**.  
  
7.  En la ventana **Propiedades**, establezca la propiedad **Text** del botón en Hello.  
  
8.  Haga doble clic en el botón para agregar el código del controlador y, en el archivo de código, agregue el código para que el controlador sea como sigue:  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. Ejecute la aplicación.  En el menú **Depurar**, haga clic en **Iniciar depuración**.  
  
 A continuación, es necesario aislar el control.  Cada componente COM utilizado por la aplicación se representa en el proyecto como una referencia COM.  Estas referencias son visibles en el nodo **Referencias** de la ventana **Explorador de soluciones**.  \(Observe que puede agregar referencias bien directamente mediante el comando **Agregar referencia** del menú **Proyecto**, o bien indirectamente, arrastrando un control ActiveX hasta el formulario\).  
  
 Los pasos siguientes explican cómo aislar el componente COM y publicar la aplicación actualizada que contiene el control aislado:  
  
##### Para aislar un componente COM  
  
1.  En el **Explorador de soluciones**, en el nodo **Referencias**, seleccione la referencia **VB6Hello**.  
  
2.  En la ventana **Propiedades**, cambie el valor de la propiedad **Aislada** de **False** a **True**.  
  
3.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
 Ahora, cuando se presiona F5, la aplicación funciona como se espera, pero se está ejecutando mediante COM sin registro.  Para demostrarlo, pruebe a eliminar del Registro el componente VB6Hello.dll y ejecutar RegFreeComDemo1.exe desde fuera del IDE de Visual Studio.  Esta vez, al hacer clic en el botón, la aplicación sigue funcionando.  Si cambia temporalmente el nombre del manifiesto de aplicación, volverá a producirse un error.  
  
> [!NOTE]
>  Puede simular la ausencia de un componente COM anulando su registro temporalmente.  Abra un símbolo del sistema, escriba `cd /d %windir%\system32` para ir a la carpeta del sistema y, a continuación, anule el registro del componente escribiendo `regsvr32 /u VB6Hello.dll`.  Puede registrarlo de nuevo escribiendo `regsvr32 VB6Hello.dll`.  
  
 El paso final es publicar la aplicación mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### Para publicar una actualización de una aplicación con un componente COM aislado  
  
1.  En el menú **Compilar**, haga clic en **Publicar RegFreeComDemo**.  
  
     Aparece el Asistente para publicación.  
  
2.  En el Asistente para publicación, especifique una ubicación en el disco del equipo local a la que tenga acceso y examine los archivos publicados.  
  
3.  Haga clic en **Finalizar** para publicar la aplicación.  
  
 Si examina los archivos publicados, observará que está incluido el archivo sysmon.ocx.  El control está completamente aislado para esta aplicación, lo que significa que si el equipo del usuario final tiene otra aplicación que utiliza una versión distinta del control, no puede interferir con esta aplicación.  
  
## Hacer referencia a ensamblados nativos  
 Visual Studio admite referencias a ensamblados nativos de Visual Basic 6.0 o de C\+\+; dichas referencias se denominan referencias nativas.  Puede saber si una referencia es nativa comprobando si su propiedad **Tipo de archivo** está establecida en **Nativo** o en **ActiveX**.  
  
 Para agregar una referencia nativa, utilice el comando **Agregar referencia** y, a continuación, vaya al manifiesto.  Algunos componentes colocan el manifiesto dentro del archivo DLL.  En este caso, puede elegir simplemente el archivo DLL y Visual Studio lo agregará como una referencia nativa si detecta que el componente contiene un manifiesto incrustado.  Visual Studio también incluirá automáticamente los archivos o ensamblados dependientes enumerados en el manifiesto si se encuentran en la misma carpeta que el componente al que se hace referencia.  
  
 El aislamiento de controles COM facilita la implementación de componentes COM que aún no tienen manifiestos.  Sin embargo, si se proporciona un componente con un manifiesto, se puede hacer referencia al manifiesto directamente.  De hecho, siempre que sea posible debería utilizar el manifiesto proporcionado por el autor del componente en lugar de utilizar la propiedad **Isolated**.  
  
## Limitaciones de la implementación de componentes COM sin registro  
 El sistema COM sin registro ofrece claras ventajas respecto a las técnicas de implementación tradicionales.  Sin embargo, existen algunas limitaciones y advertencias que también se deben señalar.  La principal limitación es que sólo funciona con Windows XP o posterior.  La implementación de componentes COM sin registro requería cambios en la forma de carga de los componentes en el sistema operativo principal.  Lamentablemente, no hay una capa de compatibilidad de nivel inferior para componentes COM sin registro.  
  
 No todos los componentes son candidatos adecuados para la implementación COM sin registro.  Un componente no es adecuado si alguna de las siguientes afirmaciones es verdadera:  
  
-   El componente es un servidor fuera de proceso.  No se admiten servidores EXE, sólo DLL.  
  
-   El componente forma parte del sistema operativo o es un componente del sistema, como XML, Internet Explorer o Microsoft Data Access Components \(MDAC\).  Debería seguir la directiva de redistribución del autor de componente; consulte a su proveedor.  
  
-   El componente forma parte de una aplicación, como Microsoft Office.  Por ejemplo, no debería intentar aislar el Modelo de objetos de Microsoft Excel.  Dicho modelo forma parte de Office y sólo se puede utilizar en equipos que tengan el producto Office completo instalado.  
  
-   El componente está pensado para su uso como complemento, por ejemplo, como un complemento de Office o como un control de un explorador web.  Tales componentes requieren normalmente algún tipo de esquema de registro definido por el entorno de host que sobrepasa el ámbito del propio manifiesto.  
  
-   El componente administra un dispositivo físico o virtual para el sistema, por ejemplo, un controlador de dispositivos para una cola de impresión.  
  
-   El componente es un acceso Data Access redistribuible.  Las aplicaciones de datos generalmente requieren la instalación de un acceso Data Access redistribuible independiente para poder ejecutarse.  No debería intentar aislar componentes como el control de datos ADO de Microsoft, Microsoft OLE DB o Microsoft Data Access Components \(MDAC\).  En su lugar, si su aplicación utiliza MDAC o SQL Server Express, debería establecerlos como requisitos previos; vea [Cómo: Instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
 En algunos casos, es posible que el desarrollador del componente lo rediseñe para el sistema COM sin registro.  Si esto no es posible, todavía puede compilar y publicar aplicaciones que dependen de ellos a través del esquema del registro estándar, utilizando el arranque.  Para obtener más información, vea [Crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md).  
  
 Los componentes COM sólo se pueden aislar una vez por cada aplicación.  Por ejemplo, no se puede aislar el mismo componente COM de dos proyectos **Biblioteca de clases** diferentes que forman parte de la misma aplicación.  De hacerlo así, se producirá una advertencia de compilación y la aplicación no se cargará en tiempo de ejecución.  Para evitar este problema, Microsoft recomienda que encapsule los componentes COM en una sola biblioteca de clases.  
  
 Hay varios escenarios donde se requiere el registro COM en el equipo del desarrollador, aun cuando la implementación de la aplicación no requiera su registro.  La propiedad `Isolated` requiere que el componente COM esté registrado en el equipo del desarrollador para generar automáticamente el manifiesto durante la compilación.  No hay ninguna función de captación del registro que inicie el registro automático durante la compilación.  Además, cualquier clase no definida explícitamente en la biblioteca de tipos no se reflejará en el manifiesto.  Al utilizar un componente COM con un manifiesto previamente existente, como por ejemplo una referencia nativa, puede que no sea necesario que el componente esté registrado en tiempo de desarrollo.  Sin embargo, el registro es necesario si el componente es un control ActiveX y desea incluirlo en el **Cuadro de herramientas** y en el Diseñador de Windows Forms.  
  
## Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)