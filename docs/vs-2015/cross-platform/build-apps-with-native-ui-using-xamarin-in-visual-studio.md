---
title: Cree aplicaciones con interfaz de usuario nativa mediante Xamarin
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
caps.latest.revision: 33
ms.author: crdun
manager: crdun
ms.openlocfilehash: 7a17f8468eca37b5b977aa6b892e268bda5376ba
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066252"
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Compilar aplicaciones con interfaz de usuario nativa mediante Xamarin en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Tras seguir los pasos de [Configuración e instalación](../cross-platform/setup-and-install.md) y [Comprobar el entorno de Xamarin](../cross-platform/verify-your-xamarin-environment.md), este tutorial le muestra cómo compilar una aplicación de Xamarin básica (mostrada a continuación) con capas de interfaz de usuario nativa. Con la interfaz de usuario nativa, el código compartido reside en una biblioteca de clases portable (PCL) y los proyectos de plataforma individuales contienen las definiciones de interfaz de usuario.

 ![Aplicación Xamarin en Android y Windows Phone](../cross-platform/media/cross-plat-xamarin-build-1.png "Cross-Plat Xamarin Build 1")

 Deberá llevar a cabo estas operaciones para compilarla:

-   [Configurar la solución](#solution)

-   [Escribir código de servicio de datos compartidos](#dataservice)

-   [Diseñar la interfaz de usuario para Android](#Android)

-   [Diseñar la interfaz de usuario para Windows Phone](#Windows)

-   [Pasos siguientes](#next)

> [!TIP]
>  Puede encontrar el código fuente completo para este proyecto en el [repositorio mobile-samples en GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
>   Si tiene dificultades o se producen errores, publique las preguntas en [forums.xamarin.com](http://forums.xamarin.com). Muchos errores pueden resolverse mediante la actualización de los últimos SDK requeridos por Xamarin, que se describen en las [Notas de la versión de Xamarin](https://developer.xamarin.com/releases/) para cada plataforma.
>
> [!NOTE]
>  La documentación para desarrolladores de Xamarin también ofrece diversos tutoriales con secciones de inicio rápido (Quickstart) y profundización (Deep Dive), como se muestra a continuación. En todas estas páginas, asegúrese de que ha seleccionado "Visual Studio" en la esquina superior derecha de la página para ver los tutoriales específicos de Visual Studio.
>
> - Aplicaciones de Xamarin con la interfaz de usuario nativa:
>
>   -   [Hello, Android](https://developer.xamarin.com/guides/android/getting_started/hello,android/) (aplicación sencilla con una pantalla)
>   -   [Hello, Android multiscreen](https://developer.xamarin.com/guides/android/getting_started/hello,android_multiscreen/) (aplicación con navegación entre pantallas)
>   -   [Android Fragments WalkThrough](http://developer.xamarin.com/guides/android/platform_features/fragments/fragments_walkthrough/) (Tutorial de fragmentos de Android, que se usa para las pantallas maestra o de detalles, entre otras cosas)
>   -   [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
>   -   [Hello, iOS Multiscreen](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS_multiscreen/)
>   -   Aplicaciones Xamarin con Xamarin.Forms (interfaz de usuario compartida)
>
>   -   [Hello, Xamarin.Forms](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms/quickstart/)
>   -   [Hello, Xamarin.Forms Multiscreen](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms-multiscreen/)

##  <a name="solution"></a> Configurar la solución
 En estos pasos, se crea una solución de Xamarin con una interfaz de usuario nativa que contiene una PCL para código compartido y dos paquetes NuGet agregados.

1. En Visual Studio, cree una nueva solución de **Aplicación en blanco (nativa portátil)** con el nombre **WeatherApp**. Puede encontrar esta plantilla con mayor facilidad si escribe **Nativa portátil** en el campo de búsqueda.

    Si no la encuentra, es posible que tenga que instalar Xamarin o habilitar la característica de Visual Studio 2015, vea [Configuración e instalación](../cross-platform/setup-and-install.md).

2. Después de hacer clic en Aceptar para crear la solución, tendrá un número de proyectos individuales:

   - **WeatherApp (Portable)**: la PCL en la que escribirá código que se comparte entre plataformas, incluida la lógica de negocios común y el código de interfaz de usuario con Xamarin.Forms.

   - **WeatherApp.Droid**: el proyecto que contiene el código nativo de Android. Este se establece como el proyecto de inicio predeterminado.

   - **WeatherApp.iOS**: el proyecto que contiene el código nativo de iOS.

   - **WeatherApp.WinPhone (Windows Phone 8.1)**: el proyecto que contiene el código nativo de Windows Phone.

     En cada proyecto nativo tiene acceso al diseñador nativo de la plataforma correspondiente y puede implementar pantallas específicas de la plataforma.

3. Agregue **Newtonsoft.Json** y el paquete NuGet al proyecto PCL, que usará para procesar la información recuperada de un servicio de datos de tiempo:

   -   En el Explorador de soluciones, haga clic con el botón derecho en **Solución "WeatherApp"** y seleccione **Administrar paquetes NuGet para la solución...**.

        En la ventana de NuGet, haga clic en la pestaña **Examinar** y busque **Newtonsoft**.

   -   Seleccione **Newtonsoft.Json**.

   -   En el lado derecho de la ventana, marque el proyecto **WeatherApp** (es el único proyecto en el que debe instalar el paquete).

   -   Asegúrese de que el campo **Versión** está establecido en la versión **estable más reciente** .

   -   Haga clic en **Instalar**.

   -   ![Localizar e instalar el paquete NuGet Newtonsoft.Json](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

4. Repita el paso 3 para buscar e instalar el paquete **Microsoft.Net.Http**.

5. Compile la solución y compruebe que no hay ningún error de compilación.

##  <a name="dataservice"></a> Escribir código de servicio de datos compartidos
 El proyecto **WeatherApp (Portable)** es en el que escribirá el código de la biblioteca de clases portable (PCL) que se comparte entre todas las plataformas. La PCL se incluye de forma automática en los paquetes de aplicaciones compilados por los proyectos de iOS, Android y Windows Phone.

 En los pasos siguientes, se agrega el código a la PCL para tener acceso y almacenar datos de ese servicio meteorológico:

1.  Para ejecutar este ejemplo, primero debe registrarse para obtener una clave de API gratuita en [http://openweathermap.org/appid](http://openweathermap.org/appid).

2.  Haga clic con el botón derecho en el proyecto **WeatherApp** y seleccione **Agregar > Clase...**. En el cuadro de diálogo **Agregar nuevo elemento** , denomine al archivo **Weather.cs**. Esta clase se usará para almacenar los datos del servicio de datos meteorológicos.

3.  Reemplace todo el contenido de **Weather.cs** por lo siguiente:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            public string Title { get; set; }
            public string Temperature { get; set; }
            public string Wind { get; set; }
            public string Humidity { get; set; }
            public string Visibility { get; set; }
            public string Sunrise { get; set; }
            public string Sunset { get; set; }

            public Weather()
            {
                //Because labels bind to these values, set them to an empty string to
                //ensure that the label appears on all platforms by default.
                this.Title = " ";
                this.Temperature = " ";
                this.Wind = " ";
                this.Humidity = " ";
                this.Visibility = " ";
                this.Sunrise = " ";
                this.Sunset = " ";
            }
        }
    }
    ```

4.  Agregue otra clase al proyecto PCL denominado **DataService.cs** que usará para procesar los datos JSON del servicio de datos meteorológicos.

5.  Reemplace todo el contenido de **DataService.cs** por el código siguiente:

    ```csharp
    using System.Threading.Tasks;
    using Newtonsoft.Json;
    using System.Net.Http;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

6.  Agregue una tercera clase a la PCL denominada **Core** en la que pondrá la lógica de negocios compartida, como la lógica que forma una cadena de consulta con un código postal, llama al servicio de datos meteorológicos y rellena una instancia de la clase **Weather** .

7.  Reemplace el contenido de **Core.cs** por lo siguiente:

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

8.  Reemplace *YOUR KEY HERE* (AÑADA AQUÍ SU CÓDIGO) en el código con la clave API obtenida en el paso 1 (todavía necesita comillas).

9. Elimine MyClass.cs en la PCL, dado que no va a usarse.

10. Compile el proyecto de PCL **WeatherApp** para asegurarse de que el código es correcto.

##  <a name="Android"></a> Diseñar la interfaz de usuario para Android
 Ahora diseñaremos la interfaz de usuario, la conectaremos al código compartido y ejecutaremos la aplicación.

### <a name="design-the-look-and-feel-of-your-app"></a>Diseñe la apariencia y el funcionamiento de su aplicación

1.  En el **Explorador de soluciones**, expanda la carpeta **WeatherApp.Droid**>**Recursos**>**diseño** y abra **Main.axml**. Esto abre el archivo en el diseñador visual. (Si aparece un error relacionado con Java, vea esta [entrada de blog](http://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).)

    > [!TIP]
    >  Hay muchos otros archivos en el proyecto. La descripción de estos archivos está fuera del alcance de este tema, pero si quiere profundizar un poco más en la estructura de un proyecto de Android, vea [Part 2 Deep Dive (Documentación exhaustiva Parte 2)](http://developer.xamarin.com/guides/android/getting_started/hello,android/hello,android_deepdive/) en el tema Hello Android en xamarin.com.

2.  Seleccione y elimine el botón predeterminado que aparece en el diseñador.

3.  Abra el Cuadro de herramientas: **Ver > Otras ventanas > Cuadro de herramientas**.

4.  En el **Cuadro de herramientas**, arrastre un control **RelativeLayout** hasta el diseñador. Usará este control como un contenedor primario para los otros controles.

    > [!TIP]
    >  Si en cualquier momento el diseño no parece mostrarse correctamente, guarde el archivo y cambie entre las pestañas **Diseño** y **Código fuente** para actualizar.

5.  En la ventana **Propiedades**, establezca la propiedad **background** (en el grupo Estilo) en `#545454`.

6.  En el **Cuadro de herramientas**, arrastre un control **TextView** hasta el control **RelativeLayout** .

7.  En la ventana **Propiedades**, establezca estas propiedades (puede ordenar la lista alfabéticamente con el botón de ordenación de la barra de herramientas de la ventana Propiedades):

    |Propiedad.|Valor|
    |--------------|-----------|
    |**text**|**Buscar por código postal**|
    |**identificador**|`@+id/ZipCodeSearchLabel`|
    |**layout_marginLeft**|`10dp`|
    |**textColor**|`@android:color/white`|
    |**textStyle**|`bold`|

    > [!TIP]
    >  Tenga en cuenta que muchas propiedades no contienen una lista desplegable de valores que pueda seleccionar.  Puede resultar difícil saber qué valor de cadena utilizar para cualquier propiedad determinada. Para obtener sugerencias, intente buscar el nombre de una propiedad en la página de la clase [R.attr](http://developer.android.com/reference/android/R.attr.html) .
    >
    >  Además, una búsqueda rápida en la web conduce generalmente a una página en [http://stackoverflow.com/](http://stackoverflow.com/), donde otras personas han usado la misma propiedad.

     Como referencia, si cambia a la vista **Código fuente**, verá el siguiente código para este elemento:

    ```xml
    <TextView
        android:text="Search by Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/ZipCodeSearchLabel"
        android:layout_centerVertical="true"
        android:layout_marginLeft="10dp"
        android:textColor="@android:color/white"
        android:textStyle="bold" />

    ```

8.  Desde el **Cuadro de herramientas**, arrastre un control **TextView** hasta el control **RelativeLayout** y colóquelo debajo del control ZipCodeSearchLabel. Para ello, se coloca el nuevo control en el borde correspondiente del control existente. Para que le resulte más fácil, amplíe un poco el diseñador.

9. En la ventana **Propiedades** , establezca estas propiedades:

    |Propiedad|Valor|
    |--------------|-----------|
    |**texto**|**Código postal**|
    |**identificador**|`@+id/ZipCodeLabel`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginTop**|`5dp`|

     El código de la vista **Código fuente** debe tener un aspecto similar al siguiente:

    ```xml
    <TextView
        android:text="Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeSearchLabel"
        android:id="@+id/ZipCodeLabel"
        android:layout_marginTop="5dp"
        android:layout_marginLeft="10dp" />
    ```

10. Desde el **Cuadro de herramientas**, arrastre un control **Number** hasta **RelativeLayout** y colóquelo debajo de la etiqueta **Código postal**. Después, establezca las siguientes propiedades:

    |Propiedad.|Valor|
    |--------------|-----------|
    |**identificador**|`@+id/zipCodeEntry`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginBottom**|`10dp`|
    |**width**|`165dp`|

     De nuevo, el código:

    ```xml
    <EditText
        android:inputType="number"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeLabel"
        android:id="@+id/zipCodeEntry"
        android:layout_marginLeft="10dp"
        android:layout_marginBottom="10dp"
        android:width="165dp" />
    ```

11. Desde el **Cuadro de herramientas**, arrastre un **Botón** hasta el control **RelativeLayout** y colóquelo a la derecha del control zipCodeEntry. Después, establezca estas propiedades:

    |Propiedad.|Valor|
    |--------------|-----------|
    |**identificador**|`@+id/weatherBtn`|
    |**texto**|**Obtener el tiempo**|
    |**layout_marginLeft**|`20dp`|
    |**layout_alignBottom**|`@id/zipCodeEntry`|
    |**width**|`165dp`|

    ```xml
    <Button    android:text="Get Weather"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/zipCodeEntry"
        android:id="@+id/weatherBtn"
        android:layout_marginLeft="20dp"
        android:layout_alignBottom="@id/zipCodeEntry"
        android:width="165dp" />
    ```

12. Ahora tiene la suficiente experiencia para crear una IU básica con el uso del diseñador de Android. También puede crear una interfaz de usuario si agrega marcado directamente al archivo .asxml de la página. Para compilar el resto de la interfaz de usuario de este modo, cambie a la vista Código fuente en el diseñador y, después, pegue el marcado siguiente *debajo* de la etiqueta `</RelativeLayout>` (sí, debajo de la etiqueta... estos elementos no se incluyen en el ReleativeLayout).

    ```xml
    <TextView
            android:text="Location"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/locationLabel"
            android:layout_marginLeft="10dp"
            android:layout_marginTop="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/locationText"
            android:layout_marginLeft="20dp"
            android:layout_marginBottom="10dp" />
        <TextView
            android:text="Temperature"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/tempLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/tempText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Wind Speed"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/windLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/windText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Humidity"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/humidtyLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/humidityText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Visibility"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/visibilityLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/visibilityText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Time of Sunrise"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunriseLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunriseText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Time of Sunset"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunsetLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunsetText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />

    ```

13. Guarde el archivo y cambie a la vista **Diseño**. Su IU aparecerá de la siguiente forma:

     ![Interfaz de usuario de la aplicación Android](../cross-platform/media/xamarin-androidui.png "Xamarin_AndroidUI")

14. Abra **MainActivity.cs** y elimine las líneas del método *OnCreate* que hacen referencia al botón predeterminado que se quitó anteriormente. Cuando termine, el código tendrá este aspecto:

    ```
    protected override void OnCreate (Bundle bundle)
    {
        base.OnCreate (bundle);

        // Set our view from the "main" layout resource
        SetContentView (Resource.Layout.Main);
    }
    ```

15. Compile el proyecto Android para comprobar su trabajo. Tenga en cuenta que la compilación agrega identificadores de control al archivo **Resource.Designer.cs** para que pueda hacer referencia a los controles por nombre en el código.

### <a name="consume-your-shared-code"></a>Use su código compartido

1.  Abra el archivo **MainActivity.cs** del proyecto **WeatherApp** en el editor de código y reemplace sus contenidos con el siguiente código. Este código llama al método `GetWeather` que usted definió en su código compartido. A continuación, en la IU de la aplicación, se muestra la información que se recupera de ese método.

    ```csharp
    using System;
    using Android.App;
    using Android.Widget;
    using Android.OS;

    namespace WeatherApp.Droid
    {
        [Activity(Label = "Sample Weather App", MainLauncher = true, Icon = "@drawable/icon")]
        public class MainActivity : Activity
        {
            protected override void OnCreate(Bundle bundle)
            {
                base.OnCreate(bundle);

                SetContentView(Resource.Layout.Main);

                Button button = FindViewById<Button>(Resource.Id.weatherBtn);

                button.Click += Button_Click;
            }

            private async void Button_Click(object sender, EventArgs e)
            {
                EditText zipCodeEntry = FindViewById<EditText>(Resource.Id.zipCodeEntry);

                if (!String.IsNullOrEmpty(zipCodeEntry.Text))
                {
                    Weather weather = await Core.GetWeather(zipCodeEntry.Text);
                    FindViewById<TextView>(Resource.Id.locationText).Text = weather.Title;
                    FindViewById<TextView>(Resource.Id.tempText).Text = weather.Temperature;
                    FindViewById<TextView>(Resource.Id.windText).Text = weather.Wind;
                    FindViewById<TextView>(Resource.Id.visibilityText).Text = weather.Visibility;
                    FindViewById<TextView>(Resource.Id.humidityText).Text = weather.Humidity;
                    FindViewById<TextView>(Resource.Id.sunriseText).Text = weather.Sunrise;
                    FindViewById<TextView>(Resource.Id.sunsetText).Text = weather.Sunset;
                }
            }
        }
    }
    ```

### <a name="run-the-app-and-see-how-it-looks"></a>Ejecute la aplicación y vea cómo funciona

1.  En el **Explorador de soluciones**, asegúrese de que el proyecto **WeatherApp.Droid** esté establecido como proyecto de inicio.

2.  Seleccione un destino de emulador o un dispositivo adecuado y después presione la tecla F5 para iniciar la aplicación.

3.  En el dispositivo o en el emulador, escriba un código postal de Estados Unidos válido en el cuadro de edición (por ejemplo: 60601) y presione **obtener tiempo**. Los datos meteorológicos de esa región aparecerán en los controles.

     ![Aplicación meteorológica para Android y Windows Phone](../cross-platform/media/xamarin-getstarted-results.png "Xamarin_GetStarted_Results")

> [!TIP]
>  El código fuente completo para este proyecto está en el [repositorio mobile-samples en GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

##  <a name="Windows"></a> Diseñar la interfaz de usuario para Windows Phone
 Ahora diseñaremos la interfaz de usuario para Windows Phone, la conectaremos al código compartido y después ejecutaremos la aplicación.

### <a name="design-the-look-and-feel-of-your-app"></a>Diseñe la apariencia y el funcionamiento de su aplicación
 El proceso de diseño de interfaces de usuario nativas de Windows Phone en una aplicación Xamarin no difiere al de cualquier otra aplicación nativa de Windows Phone. Por este motivo, no entraremos en los detalles de cómo usar el diseñador. Para eso, vea [Crear una interfaz de usuario mediante el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 En su lugar, simplemente abra MainPage.xaml y reemplace todo el código XAML con lo siguiente:

```xaml
<Page
    x:Class="WeatherApp.WinPhone.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.WinPhone"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

    <Grid>
        <StackPanel HorizontalAlignment="Left" Height="40" Margin="10,0,0,0" VerticalAlignment="Top" Width="400">
            <TextBlock x:Name="pageTitle" Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left" Height="120" Margin="10,40,0,0" VerticalAlignment="Top" Width="400" Background="#FF545454">

            <TextBlock x:Name="zipCodeSearchLabel" TextWrapping="Wrap" Text="Search by Zip Code" FontSize="18" FontWeight="Bold" HorizontalAlignment="Left" Margin="10,10,0,0"/>
            <TextBlock x:Name="zipCodeLabel" TextWrapping="Wrap" Text="Zip Code" Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>
            <StackPanel Orientation="Horizontal">
                <TextBox x:Name="zipCodeEntry" Margin="10,10,0,0" Text="" VerticalAlignment="Top" InputScope="Number" Width="165" />
                <Button x:Name="weatherBtn" Content="Get Weather" Width="165" Margin="20,0,0,0" Height="60" Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>
        <StackPanel Margin="10,175,0,0">
            <TextBlock x:Name="locationLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Location" VerticalAlignment="Top"/>
            <TextBlock x:Name="locationText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="tempLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>
            <TextBlock x:Name="tempText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="windLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Wind Speed" VerticalAlignment="Top"/>
            <TextBlock x:Name="windText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="humidityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Humidity" VerticalAlignment="Top"/>
            <TextBlock x:Name="humidityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="visibilityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>
            <TextBlock x:Name="visibilityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunriseLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunriweatherse" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunriseText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunsetLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunset" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunsetText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
        </StackPanel>
    </Grid>
</Page>
```

 En la vista del diseño, su IU debe aparecer de esta manera:

 ![Interfaz de usuario de la aplicación de Windows Phone ](../cross-platform/media/xamarin-winphone-finalui.png "Xamarin_WinPhone_FinalUI")

### <a name="consume-your-shared-code"></a>Use su código compartido

1.  En el diseñador, seleccione el botón **Obtener el tiempo** .

2.  En la ventana **Propiedades**, elija el botón de controlador de eventos (![Icono Controladores de eventos en Visual Studio](../cross-platform/media/blend-vs-eventhandlers-icon.png "blend_VS_EventHandlers_icon")).

     Este icono aparece en la esquina superior de la ventana **Propiedades** .

3.  Junto al evento **Clic** , escriba **GetWeatherButton_Click**y luego presione la tecla ENTRAR.

     Esto genera un controlador de eventos denominado `GetWeatherButton_Click`. Se abre el editor de código y coloca el cursor dentro del bloque de código del controlador de eventos.  Nota: Si no se abre el editor cuando se presiona ENTRAR, simplemente haga doble clic en el nombre del evento.

4.  Reemplace el controlador de eventos con el siguiente código:

    ```csharp
    private async void GetWeatherButton_Click(object sender, RoutedEventArgs e)
    {
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))
        {
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);
            locationText.Text = weather.Title;
            tempText.Text = weather.Temperature;
            windText.Text = weather.Wind;
            visibilityText.Text = weather.Visibility;
            humidityText.Text = weather.Humidity;
            sunriseText.Text = weather.Sunrise;
            sunsetText.Text = weather.Sunset;

            weatherBtn.Content = "Search Again";
        }
    }
    ```

     Este código llama al método `GetWeather` que usted definió en su código compartido. Este es el mismo método que usted llamó en su aplicación de Android. Además, este código muestra los datos recuperados de ese método en los controles de la IU de su aplicación.

5.  En MainPage.xaml.cs, que está abierto, elimine todo el código dentro del método **OnNavigatedTo**. Este código simplemente controla el botón predeterminado que se quitó al reemplazar el contenido de MainPage.xaml.

### <a name="run-the-app-and-see-how-it-looks"></a>Ejecute la aplicación y vea cómo funciona

1.  En el **Explorador de soluciones**, establezca el proyecto **WeatherApp.WinPhone** como el proyecto de inicio.

2.  Inicie la aplicación al presionar la tecla F5.

3.  En el emulador de Windows Phone, escriba un código postal de Estados Unidos válido en el cuadro de edición (por ejemplo: 60601) y presione **obtener tiempo**. Los datos meteorológicos de esa región aparecerán en los controles.

     ![Versión de Windows de la aplicación en ejecución](../cross-platform/media/xamarin-getstarted-results-windows.png "Xamarin_GetStarted_Results_Windows")

> [!TIP]
>  El código fuente completo para este proyecto está en el [repositorio mobile-samples en GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

##  <a name="next"></a> Pasos siguientes
 **Agregar la interfaz de usuario para iOS a la solución**

 Amplíe este ejemplo agregando una interfaz e usuario nativa para iOS. Para esto, tendrá que conectarse a un equipo Mac en la red local que tenga instalados Xcode y Xamarin. Después, puede usar el diseñador de iOS directamente en Visual Studio. Vea el [repositorio mobile-samples en GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather) para obtener una aplicación completa.

 Vea también el tutorial [Hello, iOS](http://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/hello,iOS_quickstart/) (xamarin.com). Tenga en cuenta que en esta página, debe asegurarse de que "Visual Studio" está seleccionado en la esquina superior derecha de las páginas en xamarin.com, para que aparezca el conjunto correcto de instrucciones.

 **Agregar código específico de la plataforma en el proyecto compartido**

 El código compartido en una PCL es independiente de la plataforma, porque la PCL se compila una vez y se incluye en cada paquete de aplicaciones específico de la plataforma. Si quiere escribir código compartido que use la compilación condicional para aislar el código específico de la plataforma, puede usar un proyecto *compartido*. Para obtener más detalles, vea [Code Sharing Options](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (Opciones de uso compartido de código) (xamarin.com).

## <a name="see-also"></a>Vea también
 [Desarrollo de Xamarin](http://developer.xamarin.com/) [centro de desarrollo de Windows](https://dev.windows.com/en-us) [Swift y C# Quick Reference Poster](http://aka.ms/scposter)
