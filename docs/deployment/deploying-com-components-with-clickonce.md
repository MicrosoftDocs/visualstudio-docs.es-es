---
title: Implementar componentes COM con ClickOnce | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: a63073e86c3584253e67bf4d77f43006104de075
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-com-components-with-clickonce"></a>Implementar componentes COM con ClickOnce
Implementación de componentes COM heredados ha sido tradicionalmente una tarea difícil. Los componentes tienen que ser registrados globalmente y, por tanto, pueden provocar efectos secundarios no deseados entre aplicaciones superpuestas. Normalmente esta situación no es un problema en las aplicaciones de .NET Framework porque los componentes se aíslan completamente a una aplicación o son compatibles en paralelo. Visual Studio permite implementar componentes COM aislados en Windows XP o un sistema operativo posterior.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Proporciona un mecanismo fácil y seguro para la implementación de las aplicaciones. NET. Sin embargo, si las aplicaciones utilizan componentes COM heredados, debe realizar pasos adicionales para su implementación. En este tema se describe cómo implementar componentes COM aislados y hacer referencia a componentes nativos (por ejemplo, de Visual Basic 6.0 o Visual C++).  
  
 Para obtener más información sobre cómo implementar componentes COM aislados, vea "simplificar la implementación de aplicación con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] y COM sin registro" en [http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).  
  
## <a name="registration-free-com"></a>COM sin registro  
 COM sin registro es una nueva tecnología para implementar y activar componentes COM aislados. Funciona al colocar la información del registro que normalmente se instala en el registro del sistema en un archivo XML denominado manifiesto, y biblioteca el del componente de tipos almacenados en la misma carpeta que la aplicación.  
  
 Aislar un componente COM requiere que esté registrado en el equipo del desarrollador, pero no tiene que estar registrado en el equipo del usuario final. Para aislar un componente COM, lo único que necesita hacer es establecer su referencia **Isolated** propiedad **True**. De forma predeterminada, esta propiedad se establece en **False**, que indica que debe tratarse como una referencia COM registrada. Si esta propiedad es **True**, hace que un manifiesto que se generará para este componente en tiempo de compilación. También hace que los archivos correspondientes se copien en la carpeta de la aplicación durante la instalación.  
  
 Cuando el generador del manifiesto encuentra una referencia COM aislada, enumera todas las `CoClass` las entradas de la biblioteca de tipos del componente, haciendo coincidir cada entrada con sus datos de registro correspondiente y generar manifiesto las definiciones para el de COM clases en el archivo de biblioteca de tipos.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>Implementar componentes COM sin registro mediante ClickOnce  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]tecnología de implementación es ideal para implementar componentes COM aislados, ya que ambos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] y COM sin registro requieren que un componente tiene un manifiesto para ser implementados.  
  
 Normalmente, el autor del componente debe proporcionar un manifiesto. Si no es así, sin embargo, es capaz de generar un manifiesto automáticamente para un componente COM Visual Studio. La generación del manifiesto se realiza durante la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publicar proceso; para obtener más información, vea [publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md). Esta característica también le permite aprovechar componentes heredados que crearon en los entornos de desarrollo anteriores, como Visual Basic 6.0.  
  
 Hay dos maneras que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementa los componentes COM:  
  
-   Usar al programa previo para implementar los componentes COM; Esto funciona en todas las plataformas admitidas.  
  
-   Utilice la implementación de aislamiento (también conocida como COM sin registro) de componente nativo. Sin embargo, esto solo funcionará en un Windows XP o un sistema operativo posterior.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Ejemplo de aislamiento e implementación de un componente COM Simple  
 Para demostrar la implementación de componentes COM sin registro, en este ejemplo creará una aplicación basada en Windows en Visual Basic que hace referencia a un componente COM nativo aislado creado con Visual Basic 6.0 y lo implementará mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 En primer lugar debe crear el componente COM nativo:  
  
##### <a name="to-create-a-native-com-component"></a>Para crear un componente COM nativo  
  
1.  Con Visual Basic 6.0, desde el **archivo** menú, haga clic en **New**, a continuación, **proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, seleccione la **Visual Basic** nodo y seleccione un **DLL ActiveX** proyecto. En el cuadro **Nombre**, escriba `VB6Hello`.  
  
    > [!NOTE]
    >  Solo los tipos de proyecto DLL de ActiveX y ActiveX Control son compatibles con COM sin registro; No se admiten los tipos de proyecto EXE de ActiveX ni documento ActiveX.  
  
3.  En **el Explorador de soluciones**, haga doble clic en **Class1.vb** para abrir el editor de texto.  
  
4.  En Class1.vb, agregue el código siguiente después del código generado para el `New` método:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Genere el componente. Desde el **generar** menú, haga clic en **generar solución**.  
  
> [!NOTE]
>  COM sin registro admite sólo archivos DLL y COM controla los tipos de proyecto. No puede usar a archivos exe con COM sin registro.  
  
 Ahora puede crear una aplicación basada en Windows y agregue una referencia al componente COM a él.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Para crear una aplicación basada en Windows mediante un componente COM  
  
1.  Con Visual Basic, desde el **archivo** menú, haga clic en **New**, a continuación, **proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, seleccione la **Visual Basic** nodo y seleccione **aplicación de Windows**. En el cuadro **Nombre**, escriba `RegFreeComDemo`.  
  
3.  En **el Explorador de soluciones**, haga clic en el **mostrar todos los archivos** botón para mostrar las referencias del proyecto.  
  
4.  Haga clic en el **referencias** nodo y seleccione **Agregar referencia** en el menú contextual.  
  
5.  En el **Agregar referencia** cuadro de diálogo, haga clic en el **examinar** ficha, navegue a VB6Hello.dll y, a continuación, selecciónelo.  
  
     A **VB6Hello** referencia aparece en la lista de referencias.  
  
6.  Seleccione el **cuadro de herramientas**, seleccione un **botón** controlar y arrástrelo hasta el **Form1** formulario.  
  
7.  En el **propiedades** ventana, establezca el botón **texto** propiedad **Hello**.  
  
8.  Haga doble clic en el botón para agregar el código del controlador y, en el archivo de código, agregue código para que el controlador quede como sigue:  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. Ejecute la aplicación. Desde el **depurar** menú, haga clic en **Iniciar depuración**.  
  
 A continuación debe aislar el control. Cada componente COM que usa su aplicación se representa en el proyecto como una referencia COM. Estas referencias están visibles en el **referencias** nodo en el **el Explorador de soluciones** ventana. (Tenga en cuenta que puede agregar hace referencia directamente usando el **Agregar referencia** comando el **proyecto** menú, o indirectamente al arrastrar un control ActiveX a un formulario.)  
  
 Los pasos siguientes muestran cómo aislar el componente COM y publicar la aplicación actualizada que contiene el control aislado:  
  
##### <a name="to-isolate-a-com-component"></a>Para aislar un componente COM  
  
1.  En **el Explorador de soluciones**, en la **referencias** nodo, seleccione el **VB6Hello** referencia.  
  
2.  En el **propiedades** ventana, cambie el valor de la **Isolated** propiedad de **False** a **True**.  
  
3.  Desde el **generar** menú, haga clic en **generar solución**.  
  
 Ahora, cuando se presiona F5, la aplicación funciona según lo esperado, pero ahora se ejecuta en COM sin registro. Para demostrar esto, intente anular el registro el componente VB6Hello.dll y ejecutar RegFreeComDemo1.exe fuera del IDE de Visual Studio. Esta vez cuando se hace clic en el botón, sigue funcionando. Si cambia el nombre de manifiesto de aplicación temporalmente, se producirá nuevo.  
  
> [!NOTE]
>  Puede simular la ausencia de un componente COM anulando su registro temporalmente. Abra un símbolo del sistema, vaya a la carpeta del sistema, escriba `cd /d %windir%\system32`, a continuación, anular el registro del componente escribiendo `regsvr32 /u VB6Hello.dll`. Vuelva a registrarlo escribiendo `regsvr32 VB6Hello.dll`.  
  
 El paso final es publicar la aplicación mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Para publicar una actualización de la aplicación con un componente COM aislado  
  
1.  Desde el **generar** menú, haga clic en **Publicar RegFreeComDemo**.  
  
     Aparece el Asistente para publicación.  
  
2.  En el Asistente para publicación, especifique una ubicación en los discos del equipo local donde puede obtener acceso y examine los archivos publicados.  
  
3.  Haga clic en **finalizar** para publicar la aplicación.  
  
 Si examina los archivos publicados, observará que se incluye el archivo sysmon.ocx. El control está completamente aislado para esta aplicación, lo que significa que si el equipo del usuario final tiene otra aplicación que utiliza una versión diferente del control, no puede interferir con esta aplicación.  
  
## <a name="referencing-native-assemblies"></a>Hacer referencia a ensamblados nativos  
 Visual Studio admite referencias a ensamblados de C++; o nativo de Visual Basic 6.0 dichas referencias se denominan referencias nativas. Puede saber si una referencia es nativa, compruebe que su **tipo de archivo** propiedad está establecida en **nativo** o **ActiveX**.  
  
 Para agregar una referencia nativa, utilice la **Agregar referencia** comando, a continuación, vaya al manifiesto. Algunos componentes colocan el manifiesto dentro de la DLL. En este caso, puede elegir simplemente el propio archivo DLL y Visual Studio lo agregará como una referencia nativa si detecta que el componente contiene un manifiesto incrustado. Visual Studio también incluirá automáticamente los archivos o ensamblados dependientes enumerados en el manifiesto si se encuentran en la misma carpeta que el componente que se hace referencia.  
  
 El aislamiento de controles COM resulta muy sencillo implementar componentes COM que aún no tienen manifiestos. Sin embargo, si se proporciona un componente con un manifiesto, puede hacer referencia el manifiesto directamente. De hecho, debe utilizar siempre el manifiesto proporcionado por el autor del componente siempre que sea posible en lugar de usar el **Isolated** propiedad.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Limitaciones de la implementación de componentes de COM sin registro  
 COM sin registro ofrece claras ventajas respecto a las técnicas tradicionales de implementación. Sin embargo, hay algunas limitaciones y advertencias que también deben señalar. La principal limitación es que sólo funciona en Windows XP o posterior. La implementación de COM sin registro requiere cambios en la forma en que los componentes se cargan en el sistema operativo básico. Lamentablemente, no hay ninguna capa de soporte técnico de nivel inferior para COM sin registro.  
  
 No todos los componentes son candidatos adecuados para COM sin registro. Un componente no es adecuado si se cumple alguna de las siguientes acciones:  
  
-   El componente es un servidor fuera de proceso. No se admiten servidores EXE; se admiten sólo las DLL.  
  
-   El componente forma parte del sistema operativo o es un componente del sistema, como XML, Internet Explorer o Microsoft Data Access Components (MDAC). Debe seguir la directiva de redistribución del autor del componente; Póngase en contacto con su proveedor.  
  
-   El componente forma parte de una aplicación, como Microsoft Office. Por ejemplo, no debería intentar aislar el modelo de objetos de Microsoft Excel. Esto forma parte de Office y solo puede usarse en un equipo con el producto Office completo instalado.  
  
-   El componente está diseñado para su uso como un complemento o un complemento, por ejemplo un complemento de Office o un control en un explorador Web. Dichos componentes normalmente requieren algún tipo de esquema del registro definida por el entorno de hospedaje que queda fuera del ámbito del propio manifiesto.  
  
-   El componente administra un dispositivo físico o virtual para el sistema, por ejemplo, un controlador de dispositivo para una cola de impresión.  
  
-   El componente es un acceso Data Access redistribuible. Aplicaciones de datos generalmente requieren un acceso de datos independiente redistribuible para instalarse para poder ejecutar. No debería intentar aislar los componentes como el Control de datos de Microsoft ADO, OLE DB de Microsoft o Microsoft Data Access Components (MDAC). En su lugar, si la aplicación utiliza MDAC o SQL Server Express, debe establecerlos como requisitos previos; vea [Cómo: instalar los requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
 En algunos casos, es posible que el desarrollador del componente lo rediseñe para COM sin registro. Si esto no es posible, puede generar y publicar aplicaciones que dependen de ellos a través del esquema del registro estándar mediante el programa previo. Para obtener más información, consulte [crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md).  
  
 Un componente COM sólo se pueden aislar una vez por cada aplicación. Por ejemplo, no se puede aislar el mismo componente COM desde diferentes **biblioteca de clases** proyectos que forman parte de la misma aplicación. Si lo hace, se producirá una advertencia de compilación y la aplicación no se cargará en tiempo de ejecución. Para evitar este problema, Microsoft recomienda que encapsule los componentes COM en una sola biblioteca de clases.  
  
 Hay varios escenarios en que COM se requiere el registro en el equipo del desarrollador, aunque la implementación de la aplicación no requiere el registro. El `Isolated` propiedad requiere que el componente COM esté registrado en el equipo del desarrollador para generar automáticamente el manifiesto durante la compilación. No hay ninguna función de captación de registro que invocan el registro automático durante la compilación. Además, cualquier clase no definida explícitamente en la biblioteca de tipos no se verán reflejado en el manifiesto. Cuando se usa un componente COM con un manifiesto existente, como una referencia nativa, el componente no necesite que se registrará en tiempo de desarrollo. Sin embargo, el registro es necesario si el componente es un control ActiveX y van a incluir en el **cuadro de herramientas** y el Diseñador de formularios Windows Forms.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)