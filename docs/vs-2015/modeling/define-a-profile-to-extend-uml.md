---
title: Definir un perfil para ampliar UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a495a566f78ceb2b89f8e2070837f038da352a4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918878"
---
# <a name="define-a-profile-to-extend-uml"></a>Definir un perfil para ampliar UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede definir un *Perfil de UML* para personalizar los elementos del modelo estándar con fines específicos. Un perfil define uno o varios *estereotipos de UML*. Un estereotipo se puede usar para marcar un tipo como representativo de un tipo determinado de objeto. Un estereotipo también puede extender la lista de propiedades de un elemento.

 Algunos perfiles vienen instalados con las ediciones compatibles de Visual Studio. Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Para obtener más información sobre esos perfiles y sobre cómo aplicar estereotipos, vea [personalizar el modelo con perfiles y estereotipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

 Puede definir sus propios perfiles para adaptar y ampliar UML a su propia arquitectura o área de negocio. Por ejemplo:

- Si a menudo define sitios web, podría definir un perfil propio que proporcione un estereotipo "PáginaWeb" que se pueda aplicar a las clases de los diagramas de clases. A continuación, podría utilizar diagramas de clases para planear un sitio web. Cada clase "PáginaWeb" tendría propiedades adicionales sobre el contenido de la página, el estilo, etc.

- Si desarrolla un software de banca, puede definir un perfil que proporcione un estereotipo "Cuenta". Posteriormente, podría utilizar los diagramas de clases para definir distintos tipos de cuentas y mostrar las relaciones entre ellos.

  Puede distribuir sus perfiles a los miembros de su equipo. Cada miembro del equipo puede instalar su perfil. De este modo, podrán editar y crear modelos que utilicen sus estereotipos.

> [!NOTE]
> Si aplica los estereotipos de un perfil en un modelo que está editando, y, a continuación, comparte el modelo con otras personas, estas personas deberían instalar el mismo perfil en sus equipos. De lo contrario, no podrán ver los estereotipos que ha utilizado.

 Un perfil suele ser parte de una extensión más grande [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . Por ejemplo, puede definir un comando que traduzca algunos elementos de un modelo al código. Puede definir un perfil que los usuarios deben aplicar a los paquetes que desean traducir. Este nuevo comando, junto con el perfil, se distribuiría en una sola extensión de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

 También puede definir variantes adaptadas de un perfil. Los usuarios que carguen su extensión, verán la variante que resulta apropiada para su referencia cultural.

## <a name="how-to-define-a-profile"></a><a name="DefineProfile"></a> Cómo definir un perfil

#### <a name="to-define-a-uml-profile"></a>Para definir un perfil de UML

1. Cree un nuevo archivo XML con la extensión de nombre de archivo `.profile`.

2. Agregue definiciones de estereotipos según las instrucciones descritas en [la estructura de un perfil](#Schema).

3. Agregue el perfil a una extensión de Visual Studio (archivo `.vsix`). Puede crear una nueva extensión para su perfil o agregar el perfil a una extensión existente.

     Vea la sección siguiente, [Cómo agregar un perfil a una extensión de Visual Studio](#AddProfile).

4. Instale la extensión en su equipo.

    1. Haga doble clic en el archivo de extensión, cuya extensión de nombre de archivo es `.vsix`.

    2. Reinicie Visual Studio.

5. Compruebe que se ha instalado el perfil.

    1. Seleccione el modelo en el Explorador de UML.

    2. En el ventana Propiedades, haga clic en la propiedad **perfiles** . Su perfil aparecerá en el menú. Active la marca de verificación situada junto al perfil.

    3. Seleccione el elemento para el que el perfil define los estereotipos. En el ventana Propiedades, haga clic en la propiedad **estereotipos** . Los estereotipos aparecerán en la lista. Active la marca de verificación de uno de los estereotipos.

    4. Si el perfil define propiedades adicionales para este estereotipo, expanda la propiedad para verlos.

6. Envíe el archivo de extensión a otros usuarios de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para que lo instalen en sus equipos.

## <a name="how-to-add-a-profile-to-a-visual-studio-extension"></a><a name="AddProfile"></a> Cómo agregar un perfil a una extensión de Visual Studio
 Para instalar y poder enviar un perfil a otros usuarios, debe agregar el perfil a una extensión de Visual Studio. Para obtener más información, consulte [implementación de extensiones de Visual Studio](https://msdn.microsoft.com/library/dd393694(VS.100).aspx).

#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>Para definir un perfil en una nueva extensión de Visual Studio

1. Cree un proyecto de extensión de Visual Studio.

   > [!NOTE]
   > Para utilizar este procedimiento, debe tener instalado [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

   1. En el menú **Archivo** , seleccione **Nuevo**y haga clic en **Proyecto**.

   2. En el cuadro de diálogo **nuevo proyecto** , en **plantillas instaladas**, expanda **Visual C#**, haga clic en **extensibilidad**y, a continuación, haga clic en **Proyecto VSIX**. Establezca el nombre del proyecto y haga clic en **Aceptar**.

2. Agregue su perfil al proyecto.

   - En Explorador de soluciones, haga clic con el botón secundario en el proyecto, seleccione **Agregar**y, a continuación, haga clic en **elemento existente**. En el cuadro de diálogo, busque su archivo de perfil.

3. Establezca la propiedad **Copiar en salida** del archivo de perfil.

   1. En Explorador de soluciones, haga clic con el botón secundario en el archivo de perfil y, a continuación, haga clic en **propiedades**.

   2. En el ventana Propiedades, establezca la propiedad **Copiar en el directorio de salida** en **copiar siempre**.

4. En el Explorador de soluciones, abra `source.extension.vsixmanifest`.

    El archivo se abre en el editor de manifiestos de la extensión.

5. En la página **activos** , agregue una fila que describa el perfil:

   - Haga clic en **Nueva**. Establezca los campos del cuadro de diálogo **Agregar nuevo activo** como se indica a continuación.

   - Establezca **tipo** en `Microsoft.VisualStudio.UmlProfile`

        Esta no es una de las opciones desplegables. Escriba este nombre desde el teclado.

   - Haga clic en **archivo en sistema de archivos** y seleccione el nombre del archivo de perfil, por ejemplo `MyProfile.profile`

6. Compile el proyecto.

7. Presione F5 **para depurar el perfil**.

    Se abre una instancia experimental de Visual Studio. En esta instancia, abra un proyecto de modelado. En el Explorador de UML, seleccione el elemento raíz del modelo y, en la ventana Propiedades, seleccione el perfil. A continuación, seleccione elementos dentro del modelo y establezca estereotipos que haya definido para ellos.

8. **Para extraer el archivo VSIX para la implementación**

   1. En el explorador de Windows, abra la carpeta **.\bin\Debug** o **.\bin\Release** para buscar el archivo **. vsix** . Es un archivo de la extensión de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Este archivo puede instalarse en el equipo y enviarse a otros usuarios de Visual Studio.

   2. Para instalar la extensión:

       1. Haga doble clic en el archivo `.vsix`. Se iniciará el Instalador de extensión de Visual Studio.

       2. Reinicie todas las instancias de Visual Studio que estén en ejecución.

   Si [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] no está instalado, puede utilizarse el siguiente procedimiento alternativo para extensiones pequeñas.

#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Para definir una extensión de perfil sin utilizar Visual Studio SDK

1. Cree un directorio de Windows que contenga los tres archivos siguientes:

    - *YourProfile*`.profile`

    - `extension.vsixmanifest`

    - `[Content_Types].xml` -Escriba este nombre como se muestra aquí, con los corchetes

2. Edite `[Content_Types].xml` para que contenga el texto siguiente. Observe que contiene una entrada para cada extensión de nombre de archivo.

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
      <Default Extension="profile" ContentType="application/octet-stream" />
      <Default Extension="vsixmanifest" ContentType="text/xml" />
    </Types>
    ```

3. Copie un objeto `extension.vsixmanifest` existente y modifíquelo con un editor XML. Modifique los nodos ID, Name y Content.

    - Encontrará un ejemplo de `extension.vsixmanifest` en este directorio:

         *unidad* **: \Archivos de programa\Microsoft Visual Studio [versión] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles**

    - El nodo Content será similar a:

        ```
        <Content>
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"
          >YourProfile.Profile</CustomExtension>
        </Content>
        ```

4. Comprima los tres archivos en un archivo zip.

     En el explorador de Windows, seleccione los tres archivos, haga clic con el botón secundario, seleccione **Enviar a**y, a continuación, haga clic en **carpeta comprimida (en zip)**.

5. Cambie el nombre del archivo comprimido y su extensión de nombre de archivo de `.zip` a `.vsix`.

6. Para instalar el perfil en cualquier equipo con las ediciones de Visual Studio apropiadas, haga doble clic en el archivo `.vsix`.

#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Para instalar un perfil de UML desde una extensión de Visual Studio

1. En el Explorador de Windows, haga doble clic en el archivo `.vsix` o ábralo en Visual Studio.

2. Haga clic en **instalar** en el cuadro de diálogo que aparece.

3. Para desinstalar o deshabilitar temporalmente la extensión, Abra **extensiones y actualizaciones** en el menú **herramientas** .

## <a name="how-to-define-localized-profiles"></a><a name="Localized"></a> Cómo definir perfiles localizados
 Puede definir distintos perfiles para referencias culturales o idiomas diferentes y empaquetarlos todos en la misma extensión. Cuando un usuario carga su extensión, verá el perfil que ha definido para su referencia cultural.

 Siempre debe proporcionar un perfil predeterminado. De este modo, si no ha definido un perfil para la referencia cultural del usuario, verá el perfil predeterminado.

#### <a name="to-define-a-localized-profile"></a>Para definir un perfil adaptado

1. Cree un perfil tal y como se describe en las secciones anteriores[cómo definir un perfil](#DefineProfile) y [Cómo agregar un perfil a una extensión de Visual Studio](#AddProfile). Este es el perfil predeterminado y se utiliza en cualquier instalación para la que no se proporcione un perfil adaptado.

2. Agregue un nuevo directorio en el mismo directorio del archivo de perfil predeterminado.

    > [!NOTE]
    > Si está compilando la extensión utilizando un proyecto de extensión de Visual Studio, utilice el Explorador de soluciones para agregar una nueva carpeta al proyecto.

3. Cambie el nombre del nuevo directorio al código abreviado ISO de la referencia cultural adaptada, como `bg` para búlgaro o `fr` para francés. Debe utilizar un código de referencia cultural neutro, normalmente dos letras, y no una referencia cultural concreta como `fr-CA`. Para obtener más información sobre los códigos de referencia cultural, vea [método CultureInfo. GetCultures](https://msdn.microsoft.com/library/system.globalization.cultureinfo.getcultures(VS.100).aspx), que proporciona una lista completa de códigos de referencia cultural.

4. Agregue una copia de su perfil predeterminado al nuevo directorio. No cambie el nombre de archivo.

     Una carpeta de extensión de ejemplo [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , antes de compilarse o comprimirse en un `.vsix` archivo, contendría los siguientes archivos y carpetas:

     `extension.vsixmanifest`

     `MyProfile.profile`

     `fr\MyProfile.profile`

     `de\MyProfile.profile`

    > [!NOTE]
    > No debe insertar en `extension.vsixmanifest` una referencia a las versiones localizadas de los perfiles. Los archivos del perfil copiados deben tener el mismo nombre que el perfil de la carpeta primaria.

5. Edite la nueva copia del perfil y traduzca al idioma de destino todos los elementos que estarán visibles para el usuario, como los atributos `displayName`.

6. Puede crear otras carpetas de referencia cultural y perfiles adaptados para tantas referencias culturales como desee.

7. Para compilar la extensión de Visual Studio, compile el proyecto de extensión o comprima todos los archivos, tal y como se describe en las secciones anteriores.

## <a name="the-structure-of-a-profile"></a><a name="Schema"></a> La estructura de un perfil

 Como ayuda para modificar los archivos de perfil, instale el archivo `.xsd` en:

 **%ProgramFiles%\Microsoft Visual Studio [versión] \Xml\Schemas**

 En esta sección se utiliza el perfil de C# como ejemplo. La definición completa del perfil puede verse en:

 *unidad* **: \Archivos de programa\Microsoft Visual Studio [versión] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.Profile**

 Los primeros elementos de esta ruta de acceso podrían ser diferentes a los de su instalación.

 Para obtener más información sobre el perfil de .NET, vea [estereotipos estándar para modelos UML](../modeling/standard-stereotypes-for-uml-models.md).

### <a name="main-sections-of-the-uml-profile-definition"></a>Secciones principales de la definición de un perfil de UML
 Cada perfil tiene el siguiente contenido:

```
<?xml version="1.0" encoding="utf-8"?>
<profile dslVersion="1.0.0.0"
       name="CSharpProfile" displayName="C# Profile"
       xmlns="http://schemas.microsoft.com/UML2.1.2/ProfileDefinition">
  <stereotypes>...</stereotypes>
  <metaclasses>...</metaclasses>
  <propertyTypes>...</propertyTypes>
</profile>
```

> [!NOTE]
> El atributo denominado `name` no debe contener espacios ni puntuación. El atributo `displayName`, que aparece en la interfaz de usuario, debe ser una cadena XML válida.

 Cada perfil contiene tres secciones principales. En orden inverso, son las siguientes:

- `<propertyTypes>` : una lista de tipos que se utilizan para las propiedades definidas en la sección de estereotipos.

- `<metaclasses>`: una lista de los tipos de elementos del modelo a los que se aplican los estereotipos de este perfil, como por ejemplo, IClass, IInterface, IOperation e IDependency.

- `<stereotypes>` : las definiciones de estereotipo. Cada definición incluye los nombres y tipos de propiedades que se agregan al elemento del modelo de destino.

#### <a name="property-types"></a>Tipos de propiedades
 `<propertyTypes>`En la sección se declara una lista de tipos que se utilizan para las propiedades de la `<stereotypes>` sección. Existen dos tipos de propiedades: tipos externos y tipos de enumeración.

 Un tipo externo declara el nombre completo de un tipo de .NET estándar:

```
<externalType name="System.String" />
```

 Un tipo de enumeración define un conjunto de valores literales:

```
<enumerationType name="PackageVisibility">
  <enumerationLiterals>
    <enumerationLiteral name="internal" displayName="internal"  />
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />
  </enumerationLiterals>
</enumerationType>
```

#### <a name="metaclasses"></a>Metaclases
 La sección `<metaclasses>` contiene una lista de los tipos de elementos del modelo para los que se pueden definir estereotipos de este perfil:

```
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />
```

 Para obtener la lista completa de los tipos de relación y elemento de modelo que puede usar como metaclases, vea [tipos de elemento de modelo](#Elements).

#### <a name="stereotype-definition"></a>Definición de estereotipos
 La sección `<stereotypes>` contiene una o varias definiciones de estereotipos:

```
<stereotype name="CSharpClass" displayName="C# Class"> ...
```

 En cada estereotipo se muestran uno o varios tipos de relaciones o elementos del modelo a los que se puede aplicar. Puede especificar el nombre de un tipo base para que incluya todos sus tipos derivados. Por ejemplo, si especifica `Microsoft.VisualStudio.Uml.Classes.IType`, el estereotipo podrá aplicarse a `IClass`, `IInterface`, `IEnumeration` y algunos otros tipos de elementos.

```
<metaclasses>
  <metaclassMoniker name=
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />
</metaclasses>
```

 El atributo `name` de `metaclassMoniker` es un vínculo a un elemento de la sección `<metaClasses>`.

> [!NOTE]
> El nombre del moniker debe comenzar con `/yourProfileName/`, donde `yourProfileName` se define en el atributo `name` del perfil ("CSharpProfile" en este ejemplo). El moniker finaliza con el nombre de una de las entradas de la sección de metaclases.

 En cada estereotipo se pueden mostrar cero o más propiedades que se agregan a cualquier elemento del modelo al que se aplica el estereotipo. `<propertyType>`Contiene un vínculo a uno de los tipos que se definen en la `<propertyTypes>` sección. El vínculo debe ser `<externalTypeMoniker>` para que haga referencia a `<externalType>,` o `<enumerationTypeMoniker>` para que haga referencia a `<enumerationType>`. De nuevo, el vínculo comienza con el nombre del perfil.

```
  <properties>
    <property name="IsStatic"
            displayName="Is Static" defaultValue="false">
      <propertyType>
<externalTypeMoniker
               name="/CSharpProfile/System.Boolean" />
      </propertyType>
    </property>
    <property name="PackageVisibility"
              displayName="Package Visibility"
              defaultValue="internal">
      <propertyType>
        <enumerationTypeMoniker
              name="/CSharpProfile/PackageVisibility"/>
      </propertyType>
    </property>
  </properties>
</stereotype>
```

## <a name="model-element-types"></a><a name="Elements"></a> Tipos de elementos de modelo
 El conjunto de tipos para los que puede definir estereotipos se muestra en [tipos de elementos del modelo UML](../modeling/uml-model-element-types.md).

## <a name="troubleshooting"></a>Solución de problemas
 Los estereotipos no aparecen en los modelos UML.
Tiene que seleccionar el perfil en un paquete o modelo. A continuación, los estereotipos aparecerán en elementos dentro del paquete o modelo. Para obtener más información, vea [Agregar estereotipos a elementos del modelo UML](../modeling/add-stereotypes-to-uml-model-elements.md).

 Aparece el siguiente error al abrir un modelo UML: **VS1707: no se pueden cargar los siguientes perfiles porque se produjo un error de serialización: perprofile. Profile**
1. Compruebe que la sintaxis XML básica de .profile es correcta.

2. Asegúrese de que cada nombre del Moniker tiene el formato /profileName/nodeName. ProfileName es el valor del atributo de nombre en el nodo de perfil raíz. NodeName es el valor del atributo de nombre de una metaclase, externalType o enumerationType.

3. Asegúrese de que la sintaxis es como se describe aquí y como se muestra en _unidad_**: \Archivos de programa\Microsoft Visual Studio [ \\ versión] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles**.

4. Desinstale la extensión defectuosa. En el menú **Herramientas**, haga clic en **Extensiones y actualizaciones**.

   - Si no aparece la extensión, vea el elemento siguiente.

5. Recompile el archivo VSIX y ábralo en el Explorador de Windows para reinstalarlo. Reinicie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

   La extensión no aparece en el administrador de extensiones, pero cuando intenta volver a instalarla, aparece el siguiente mensaje: **la extensión ya está instalada en todos los productos aplicables.**
   1. Quitar el archivo de extensión de una subcarpeta de *LocalAppData*\Microsoft\VisualStudio \\ [versión] \Extensions\

   - Para ver *LocalAppData*, debe establecer Mostrar archivos y carpetas ocultos en la pestaña ver de opciones de carpeta del explorador de Windows.

   - *LocalAppData* suele estar en C:\Users \\ *username*\AppData\Local\

6. Reinicie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="see-also"></a>Consulte también
 [Agregar estereotipos a elementos del modelo UML](../modeling/add-stereotypes-to-uml-model-elements.md) [personalizar el modelo con perfiles y estereotipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [ESTEREOTIPOs estándar para modelos UML](../modeling/standard-stereotypes-for-uml-models.md)
 