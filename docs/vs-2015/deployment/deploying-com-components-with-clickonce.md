---
title: Implementar componentes COM con ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 870255afe466709f8e9a5fc48e5135943443900d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002757"
---
# <a name="deploying-com-components-with-clickonce"></a>Implementar componentes COM con ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Implementación de componentes COM heredados ha sido tradicionalmente una tarea difícil. Los componentes deben estar registrados globalmente y, por tanto, pueden provocar efectos secundarios no deseados entre aplicaciones que se superponen. Por lo general esta situación no es un problema en las aplicaciones de .NET Framework porque los componentes están completamente aislados para una aplicación o son compatibles en paralelo. Visual Studio permite implementar los componentes COM aislados en Windows XP o en un sistema operativo posterior.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Proporciona un mecanismo fácil y seguro para la implementación de las aplicaciones. NET. Sin embargo, si las aplicaciones utilizan componentes COM heredados, necesitará realizar pasos adicionales para su implementación. Este tema describe cómo implementar componentes COM aislados y hacer referencia a componentes nativos (por ejemplo, desde Visual Basic 6.0 o Visual C++).  
  
 Para obtener más información sobre la implementación de componentes COM aislados, consulte "Simplifique la implementación de aplicaciones con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] y COM sin registro" en [ https://msdn.microsoft.com/magazine/msdn-magazine-issues.aspx ](https://msdn.microsoft.com/magazine/msdn-magazine-issues.aspx).  
  
## <a name="registration-free-com"></a>COM sin registro  
 COM sin registro es una nueva tecnología para implementar y activar los componentes COM aislados. Funciona mediante la colocación de la biblioteca de tipos de todos los del componente y la información de registro que se suele instalar en el registro del sistema en un archivo XML denominado manifiesto, almacenados en la misma carpeta que la aplicación.  
  
 Aislar un componente COM requiere que esté registrado en el equipo del desarrollador, pero no tiene que estar registrado en el equipo del usuario final. Para aislar un componente COM, todo lo que necesita hacer es establecer su referencia **aislado** propiedad **True**. De forma predeterminada, esta propiedad se establece en **False**, que indica que debe tratarse como una referencia COM registrada. Si esta propiedad es **True**, hace que un manifiesto que se generará para este componente en tiempo de compilación. También hace que los archivos correspondientes se copien en la carpeta de aplicación durante la instalación.  
  
 Cuando el generador del manifiesto encuentra una referencia COM aislada, enumera todos los `CoClass` las entradas de la biblioteca de tipos del componente, haciendo coincidir cada entrada con sus datos de registro correspondientes y la generación de manifiesto las definiciones para el de COM clases en el archivo de biblioteca de tipos.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>Implementar componentes COM sin registro mediante ClickOnce  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tecnología de implementación es adecuada para implementar componentes COM aislados, porque ambos [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] y COM sin registro requieren que un componente tiene un manifiesto para ser implementados.  
  
 Normalmente, el autor del componente debe proporcionar un manifiesto. Si no es así, sin embargo, es capaz de generar un manifiesto automáticamente para un componente COM de Visual Studio. La generación del manifiesto se realiza durante la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] proceso de publicación; para obtener más información, vea [publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md). Esta característica también le permite aprovechar los componentes heredados que crearon en entornos de desarrollo anteriores como Visual Basic 6.0.  
  
 Hay dos maneras que [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementa los componentes COM:  
  
-   Usar al programa previo para implementar los componentes COM; Esto funciona en todas las plataformas compatibles.  
  
-   Utilice la implementación de aislamiento (también conocido como COM sin registro) de componente nativo. Sin embargo, esto solo funcionará en un Windows XP o en un sistema operativo posterior.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Ejemplo de aislamiento e implementación de un componente COM sencillo  
 Para demostrar la implementación de componentes COM sin registro, en este ejemplo creará una aplicación basada en Windows en Visual Basic que hace referencia a un componente COM nativo aislado creado con Visual Basic 6.0 e implementarla mediante [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
 En primer lugar debe crear el componente COM nativo:  
  
##### <a name="to-create-a-native-com-component"></a>Para crear un componente COM nativo  
  
1.  Con Visual Basic 6.0, desde el **archivo** menú, haga clic en **New**, a continuación, **proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, seleccione el **Visual Basic** nodo y seleccione un **DLL ActiveX** proyecto. En el cuadro **Nombre** , escriba `VB6Hello`.  
  
    > [!NOTE]
    >  Solo los tipos de proyecto DLL de ActiveX y controles ActiveX son compatibles con COM sin registro; No se admiten los tipos de proyecto EXE de ActiveX y documento ActiveX.  
  
3.  En **el Explorador de soluciones**, haga doble clic en **Class1.vb** para abrir el editor de texto.  
  
4.  En Class1.vb, agregue el código siguiente después del código generado para el `New` método:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Genere el componente. Desde el **compilar** menú, haga clic en **compilar solución**.  
  
> [!NOTE]
>  COM sin registro admite solo los archivos DLL y COM controla los tipos de proyecto. No se puede usar a archivos exe con COM sin registro.  
  
 Ahora puede crear una aplicación basada en Windows y agregue una referencia al componente COM a él.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Para crear una aplicación basada en Windows mediante un componente COM.  
  
1. Con Visual Basic, desde el **archivo** menú, haga clic en **New**, a continuación, **proyecto**.  
  
2. En el **nuevo proyecto** cuadro de diálogo, seleccione el **Visual Basic** nodo y seleccione **aplicación Windows**. En el cuadro **Nombre** , escriba `RegFreeComDemo`.  
  
3. En **el Explorador de soluciones**, haga clic en el **mostrar todos los archivos** botón para mostrar las referencias del proyecto.  
  
4. Haga clic en el **referencias** nodo y seleccione **Agregar referencia** en el menú contextual.  
  
5. En el **Agregar referencia** cuadro de diálogo, haga clic en el **examinar** pestaña, navegue a VB6Hello.dll y, a continuación, selecciónelo.  
  
    Un **VB6Hello** referencia aparece en la lista de referencias.  
  
6. Elija la **cuadro de herramientas**, seleccione un **botón** controlar y arrástrelo hasta el **Form1** formulario.  
  
7. En el **propiedades** ventana, establezca el botón **texto** propiedad **Hello**.  
  
8. Haga doble clic en el botón para agregar el código del controlador y, en el archivo de código, agregue código para que el controlador quede como sigue:  
  
   ```  
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim VbObj As New VB6Hello.Class1  
       VbObj.SayHello()  
   End Sub  
   ```  
  
9. Ejecute la aplicación. Desde el **depurar** menú, haga clic en **Iniciar depuración**.  
  
   A continuación debe aislar el control. Cada componente COM que usa su aplicación se representa en el proyecto como una referencia COM. Estas referencias están visibles en el **referencias** nodo en el **el Explorador de soluciones** ventana. (Tenga en cuenta que puede agregar referencias directamente utilizando el **Agregar referencia** comando el **proyecto** menú, o indirectamente, arrastre un control ActiveX a su formulario.)  
  
   Los pasos siguientes muestran cómo aislar el componente COM y publicar la aplicación actualizada que contiene el control aislado:  
  
##### <a name="to-isolate-a-com-component"></a>Para aislar un componente COM  
  
1. En **el Explorador de soluciones**, en el **referencias** nodo, seleccione el **VB6Hello** referencia.  
  
2. En el **propiedades** ventana, cambie el valor de la **aislado** propiedad desde **False** a **True**.  
  
3. Desde el **compilar** menú, haga clic en **compilar solución**.  
  
   Ahora, cuando presione F5, la aplicación funciona según lo previsto, pero ahora se está ejecutando en COM sin registro. Para probarlo, intente anular el registro del componente VB6Hello.dll y ejecutar RegFreeComDemo1.exe fuera del IDE de Visual Studio. Esta vez cuando se hace clic en el botón, sigue funcionando. Si cambie temporalmente el nombre del manifiesto de aplicación, se producirá a intentarlo.  
  
> [!NOTE]
>  Puede simular la ausencia de un componente COM eliminando temporalmente. Abra un símbolo del sistema, vaya a la carpeta del sistema escribiendo `cd /d %windir%\system32`, a continuación, anular el registro del componente escribiendo `regsvr32 /u VB6Hello.dll`. Vuelva a registrarlo escribiendo `regsvr32 VB6Hello.dll`.  
  
 El último paso es publicar la aplicación mediante [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Para publicar una actualización de la aplicación con un componente COM aislado  
  
1. Desde el **compilar** menú, haga clic en **Publicar RegFreeComDemo**.  
  
    Aparece el Asistente para publicación.  
  
2. En el Asistente para publicación, especifique una ubicación en los discos del equipo local donde puede acceder y examine los archivos publicados.  
  
3. Haga clic en **Finalizar** para publicar la aplicación.  
  
   Si examina los archivos publicados, observará que se incluye el archivo sysmon.ocx. El control está completamente aislado para esta aplicación, lo que significa que si el equipo del usuario final tiene otra aplicación que utilice una versión diferente del control, no puede interferir con esta aplicación.  
  
## <a name="referencing-native-assemblies"></a>Hacer referencia a ensamblados nativos  
 Visual Studio admite referencias a ensamblados de C++; o nativo de Visual Basic 6.0 Estas referencias se denominan referencias nativas. Puede indicar si una referencia es nativa mediante la comprobación de que su **tipo de archivo** propiedad está establecida en **nativo** o **ActiveX**.  
  
 Para agregar una referencia nativa, utilice el **Agregar referencia** comando y, después, busque el manifiesto. Algunos componentes colocan el manifiesto dentro de la DLL. En este caso, simplemente puede elegir el propio archivo DLL y Visual Studio lo agregará como una referencia nativa si detecta que el componente contiene un manifiesto incrustado. Visual Studio también incluirá automáticamente los archivos dependientes o ensamblados enumerados en el manifiesto si se encuentran en la misma carpeta que el componente que se hace referencia.  
  
 Aislamiento del control COM facilita implementar componentes COM que aún no tienen manifiestos. Sin embargo, si se proporciona un componente con un manifiesto, puede hacer referencia el manifiesto directamente. De hecho, siempre debe usar el manifiesto proporcionado por el autor del componente siempre que sea posible en lugar de usar el **aislado** propiedad.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Limitaciones de implementación de componentes de COM sin registro  
 COM sin registro proporciona claras ventajas sobre técnicas de implementación tradicionales. Sin embargo, hay algunas limitaciones y advertencias que también deben señalar. La principal limitación es que sólo funciona en Windows XP o versiones posteriores. La implementación de COM sin registro requiere cambios en la forma en que se cargan los componentes en el sistema operativo principal. Lamentablemente, no hay ningún nivel de soporte técnico de nivel inferior para COM sin registro.  
  
 No todos los componentes son candidatos adecuados para COM sin registro. Un componente no es adecuado si se cumple alguna de las siguientes acciones:  
  
- El componente es un servidor fuera de proceso. No se admiten servidores EXE; se admiten sólo las DLL.  
  
- El componente forma parte del sistema operativo, o es un componente del sistema, como XML, Internet Explorer o Microsoft Data Access Components (MDAC). Debe seguir la directiva de redistribución del autor del componente; Póngase en contacto con su proveedor.  
  
- El componente forma parte de una aplicación, como Microsoft Office. Por ejemplo, no debe intentar aislar el modelo de objetos de Microsoft Excel. Esto forma parte de Office y solo puede usarse en un equipo con el producto Office completo instalado.  
  
- El componente está diseñado para su uso como un complemento o un complemento, por ejemplo un complemento de Office o un control en un explorador Web. Dichos componentes normalmente requieren algún tipo de esquema del registro definida por el entorno de hospedaje que queda fuera del ámbito del propio manifiesto.  
  
- El componente administra un dispositivo físico o virtual para el sistema, por ejemplo, un controlador de dispositivo para una cola de impresión.  
  
- El componente es un acceso a datos redistribuible. Aplicaciones de datos generalmente requieren un acceso de datos independiente redistribuible instalarse antes de poder ejecutarlos. No debe intentar aislar componentes como el Control de datos de Microsoft ADO, OLE DB de Microsoft o Microsoft Data Access Components (MDAC). En su lugar, si la aplicación utiliza MDAC o SQL Server Express, debe establecerlos como requisitos previos; vea [Cómo: Instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
  En algunos casos, es posible para el desarrollador del componente cambiar el diseño de COM sin registro. Si esto no es posible, puede generar y publicar aplicaciones que dependen de ellos a través del esquema del registro estándar mediante el programa previo. Para obtener más información, consulte [crear paquetes de programa previo](../deployment/creating-bootstrapper-packages.md).  
  
  Un componente COM solo se pueden aislar una vez por cada aplicación. Por ejemplo, no se puede aislar el mismo componente COM desde dos diferentes **biblioteca de clases** proyectos que forman parte de la misma aplicación. Si lo hace, se producirá una advertencia de compilación y la aplicación no se cargará en tiempo de ejecución. Para evitar este problema, Microsoft recomienda que encapsule los componentes COM en una sola biblioteca de clases.  
  
  Hay varios escenarios en que COM es necesario registrarse en el equipo del desarrollador, aunque la implementación de la aplicación no requiere el registro. El `Isolated` propiedad requiere que el componente COM esté registrado en el equipo del desarrollador para generar automáticamente el manifiesto durante la compilación. No hay ninguna función de captación del registro que invocar el registro automático durante la compilación. Además, cualquier clase no definida explícitamente en la biblioteca de tipos no se reflejarán en el manifiesto. Cuando se usa un componente COM con un manifiesto existente, como una referencia nativa, el componente no deba registrarse en tiempo de desarrollo. Sin embargo, se debe registrar el componente es un control ActiveX y van a incluir en el **cuadro de herramientas** y el Diseñador de Windows Forms.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)
