---
title: Compilar aplicaciones con interfaz de usuario nativa mediante Xamarin en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 3475bfff07b64c171b506ff1cefaee6c8e55cdda
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381086"
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Compilar aplicaciones con interfaz de usuario nativa mediante Xamarin en Visual Studio

La mayoría de los desarrolladores que eligen Xamarin y C# para escribir aplicaciones móviles multiplataforma utilizan Xamarin.Forms. Xamarin.Forms define una interfaz de usuario que se asigna a los controles nativos de iOS, Android y la Plataforma universal de Windows (UWP). Xamarin.Forms se describe en el artículo [Información sobre los conceptos básicos de la compilación de aplicaciones con Xamarin.Forms en Visual Studio](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).

En este artículo se describe un enfoque diferente que implica el acceso a las API de la interfaz de usuario nativa de cada plataforma. Trabajar con las API nativas es un enfoque mucho más difícil que Xamarin.Forms porque requiere amplios conocimientos sobre cada plataforma. La ventaja es que puede personalizar la interfaz de usuario de acuerdo con los puntos fuertes y las capacidades determinados de cada plataforma, mientras se continúa compartiendo la lógica empresarial subyacente.

Tras seguir los pasos de [Configuración e instalación](../cross-platform/setup-and-install.md) y [Comprobar el entorno de Xamarin](../cross-platform/verify-your-xamarin-environment.md), este tutorial le muestra cómo compilar una aplicación de Xamarin básica con capas de interfaz de usuario nativa. Con la interfaz de usuario nativa, el código compartido reside en una biblioteca de .NET Standard y los proyectos de plataforma individuales contienen las definiciones de interfaz de usuario. Esta es la aplicación que va a compilar ejecutándose (de izquierda a derecha) en teléfonos iOS y Android y en equipos Windows 10 de escritorio.

![Aplicación Xamarin en iOS, Android y Windows](../cross-platform/media/cross-plat-xamarin-build-1-Large.png#lightbox)

Deberá llevar a cabo estas operaciones para compilarla:

- [Configurar la solución](#solution)

- [Escribir código de servicio de datos compartidos](#dataservice)

- [Diseñar la interfaz de usuario para Android](#Android)

- [Diseñar la interfaz de usuario para Windows](#Windows)

- [Pasos siguientes](#next), que incluyen diseñar una interfaz de usuario de iOS

> [!TIP]
> Puede encontrar el código fuente completo para este proyecto en el [repositorio mobile-samples en GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
> Si tiene dificultades o se producen errores, publique las preguntas en [forums.xamarin.com](http://forums.xamarin.com). Muchos errores pueden resolverse mediante la actualización de los últimos SDK requeridos por Xamarin, que se describen en las [Notas de la versión de Xamarin](https://developer.xamarin.com/releases/) para cada plataforma.

> [!NOTE]
> La documentación para desarrolladores de Xamarin también ofrece diversos tutoriales con secciones de inicio rápido (Quickstart) y profundización (Deep Dive), como se muestra a continuación. En todas estas páginas, asegúrese de que ha seleccionado "Visual Studio" para ver los tutoriales específicos de Visual Studio.
>
>  -   Aplicaciones de Xamarin con la interfaz de usuario nativa:
>     -   [Hello, Android](/xamarin/android/get-started/hello-android/) (aplicación sencilla con una pantalla)
>     -   [Hello, Android multiscreen](/xamarin/android/get-started/hello-android-multiscreen/) (aplicación con navegación entre pantallas)
>     -   [Android Fragments WalkThrough](/xamarin/android/platform/fragments/implementing-with-fragments/) (Tutorial de fragmentos de Android, que se usa para las pantallas maestra o de detalles, entre otras cosas)
>     -   [Hello, iOS](/xamarin/ios/get-started/hello-iOS/)
>     -   [Hello, iOS Multiscreen](/xamarin/ios/get-started/hello-iOS-multiscreen/)

>  -   Aplicaciones Xamarin con Xamarin.Forms (interfaz de usuario compartida)
>     -   [Hello, Xamarin.Forms](/xamarin/xamarin-forms/get-started/hello-xamarin-forms/quickstart/)
>     -   [Hello, Xamarin.Forms Multiscreen](/xamarin/xamarin-forms/get-started/hello-xamarin-forms-multiscreen/)

<a name="solution" />

##  <a name="set-up-your-solution"></a>Configurar la solución

Visual Studio no tiene una plantilla de solución para crear aplicaciones de interfaz de usuario nativas mediante el uso compartido de una biblioteca de .NET Standard. Sin embargo, no es difícil crear una solución de este tipo a partir de los proyectos individuales. Estos pasos crean una solución de Xamarin con proyectos para cada tipo de plataforma de aplicaciones y una biblioteca de .NET Standard para el código compartido.

1.  En Visual Studio, cree una nueva solución de **biblioteca de clases (.NET Standard)** con el nombre **WeatherApp**. La manera más sencilla de encontrar esta plantilla es seleccionar **Visual C#** a la izquierda y, a continuación, **.NET Standard**:

    ![Crear la solución de .NET Standard](../cross-platform/media/cross-plat-xamarin-build-2.png)

    Tras hacer clic en Aceptar, la solución **WeatherApp** consta de un solo proyecto denominado **WeatherApp**.

2.  Si quiere utilizar iOS como destino, agregue un proyecto de iOS a la solución. Haga clic con el botón derecho en el nombre de la solución en el **Explorador de soluciones** y seleccione **Agregar** y **Nuevo proyecto**.  En el cuadro de diálogo **Nuevo proyecto**, a la izquierda, seleccione **Visual C#** y, a continuación, **iOS** y **Universal**. (Si no la encuentra ahí, es posible que tenga que instalar Xamarin o habilitar la característica de Visual Studio 2017; consulte [Configuración e instalación](../cross-platform/setup-and-install.md)). En la lista de plantillas, seleccione **Aplicación de vista única (iOS)**. Asígnele el nombre **WeatherApp.iOS**.

3.  Si quiere utilizar Android como destino, agregue un proyecto de Android a la solución. En el cuadro de diálogo **Nuevo proyecto**, a la izquierda, seleccione **Visual C#** y **Android**. En la lista de plantillas, seleccione **Aplicación vacía (Android)**. Asígnele el nombre **WeatherApp.Android**.

4. Si desea utilizar la Plataforma universal de Windows como destino, en el cuadro de diálogo **Nuevo proyecto**, a la izquierda, seleccione **Visual C#** y **Windows Universal**. En la lista de plantillas, seleccione **Aplicación vacía (Windows universal)** y asígnele el nombre **WeatherApp.UWP**.

5. Para cada uno de los proyectos de aplicación (iOS, Android y UWP), haga clic con el botón derecho en la sección **Referencias** en el **Explorador de soluciones** y seleccione **Agregar referencia**. En el cuadro de diálogo **Administrador de referencias**, a la izquierda, seleccione **Proyecto** y **Solución**. Verá una lista de todos los proyectos de la solución, excepto el proyecto cuyas referencias está administrando:

   ![Establecer una referencia al proyecto de .NET Standard](../cross-platform/media/cross-plat-xamarin-build-3.png)

   Marque la casilla situada junto a **WeatherApp**.

   Después de marcar esta casilla para cada uno de los proyectos de aplicación, todos los proyectos contienen referencias a la biblioteca de .NET Standard y pueden compartir el código en esa biblioteca.

6. Agregue el paquete NuGet **Newtonsoft.Json** al proyecto de .NET Standard, que usará para procesar la información recuperada de un servicio de datos meteorológicos:

    -   Haga clic con el botón derecho en **WeatherApp** en el **Explorador de soluciones** y seleccione **Administrar paquetes NuGet...**.

         En la ventana de NuGet, haga clic en la pestaña **Examinar** y busque **Newtonsoft**.

    -   Seleccione **Newtonsoft.Json**.

    -   Asegúrese de que el campo **Versión** está establecido en la versión **estable más reciente** .

    -   Haga clic en **Instalar**.

7.  Repita el paso 6 para buscar e instalar el paquete **Microsoft.CSharp** en el proyecto de .NET Standard. Esta biblioteca es necesaria para utilizar el tipo de datos `dynamic` de C# en una biblioteca de .NET Standard.

8.  Compile la solución y compruebe que no hay ningún error de compilación.

<a name="dataservice" />

## <a name="write-shared-data-service-code"></a>Escribir código de servicio de datos compartidos

 El proyecto **WeatherApp** es la biblioteca de .NET Standard. Este proyecto es donde escribirá el código que se comparte entre todas las plataformas. Dado que cada proyecto de aplicación tiene una referencia a la biblioteca de .NET Standard, la biblioteca se incluye con los paquetes de las aplicaciones iOS, Android y UWP.

 En los pasos siguientes se agrega el código a la biblioteca de .NET Standard para tener acceso a los datos de ese servicio meteorológico y almacenarlos:

1.  En primer lugar, regístrese para obtener una clave de API de tiempo gratuita en [http://openweathermap.org/appid](http://openweathermap.org/appid). Esta clave de API permitirá que la aplicación obtenga la información meteorológica de cualquier código postal de Estados Unidos. (No funciona para los códigos postales de fuera de Estados Unidos).

2.  Haga clic con el botón derecho en el proyecto **WeatherApp** y seleccione **Agregar > Clase...**. En el cuadro de diálogo **Agregar nuevo elemento** , denomine al archivo *Weather.cs*. Esta clase se usará para almacenar los datos del servicio de datos meteorológicos.

3.  Reemplace todo el contenido de *Weather.cs* por el código siguiente:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            // Because labels bind to these values, set them to an empty string to
            // ensure that the label appears on all platforms by default.
            public string Title { get; set; } = " ";
            public string Temperature { get; set; } = " ";
            public string Wind { get; set; } = " ";
            public string Humidity { get; set; } = " ";
            public string Visibility { get; set; } = " ";
            public string Sunrise { get; set; } = " ";
            public string Sunset { get; set; } = " ";
        }
    }
    ```

4.  Agregue otra clase al proyecto .NET Standard denominado `DataService.cs`. Esta clase se usará para procesar los datos JSON del servicio de datos meteorológicos.

5.  Reemplace todo el contenido de *DataService.cs* por el código siguiente:

    ```csharp
    using System.Net.Http;
    using System.Threading.Tasks;
    using Newtonsoft.Json;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> GetDataFromService(string queryString)
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

6.  Agregue una tercera clase a la biblioteca de .NET Standard denominada *Core.cs*. Utilizará esta clase para formar una cadena de consulta con un código postal, llamar al servicio de datos meteorológicos y rellenar una instancia de la clase **Weather**.

7.  Reemplace el contenido de *Core.cs* por el código siguiente:

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
                string key = "YOUR API KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }

                dynamic results = await DataService.GetDataFromService(queryString).ConfigureAwait(false);

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

8. Reemplace la primera aparición de *YOUR API KEY HERE* por la clave de API que obtuvo en el paso 1. No se olvide de entrecomillarla.

9. Elimine *MyClass.cs* en la biblioteca de .NET Standard porque no se utilizará.

10. Compile el proyecto **WeatherApp** para asegurarse de que el código es correcto.

<a name="Android" />

## <a name="design-ui-for-android"></a>Diseñar la interfaz de usuario para Android

 Ahora puede diseñar la interfaz de usuario, conectarla al código compartido y, a continuación, ejecutar la aplicación.

### <a name="design-the-look-and-feel-of-your-app"></a>Diseñe la apariencia y el funcionamiento de su aplicación

1.  En el **Explorador de soluciones**, expanda la carpeta **WeatherApp.Droid > Recursos > diseño** y abra *Main.axml*. Este comando abre el archivo en el diseñador visual. (Si aparece un error relacionado con Java, vea esta [entrada de blog](http://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).)

    > [!TIP]
    >  Hay muchos otros archivos en el proyecto. La descripción de estos archivos está fuera del alcance de este artículo, pero si quiere profundizar un poco más en la estructura de un proyecto de Android, consulte [Parte 2: análisis detallado](/xamarin/android/get-started/hello-android/hello-android-deepdive/) en el artículo sobre Hola, Android.

2.  Abra el Cuadro de herramientas: **Ver > Otras ventanas > Cuadro de herramientas**.

3.  En el **Cuadro de herramientas**, arrastre un control **RelativeLayout** hasta el diseñador. Usará este control como un contenedor primario para los otros controles.

    > [!TIP]
    >  Si en cualquier momento el diseño no parece mostrarse correctamente, guarde el archivo y cambie entre las pestañas **Diseño** y **Código fuente** para actualizar.

4.  En la ventana **Propiedades**, establezca la propiedad **background** (en el grupo Estilo) en `#545454`.  Asegúrese por el título de la ventana **Propiedades** que está configurando el fondo de **RelativeLayout**.

5.  En el **Cuadro de herramientas**, arrastre un control **TextView** hasta el control **RelativeLayout** .

6.  En la ventana **Propiedades**, establezca estas propiedades. (Puede ser útil ordenar la lista alfabéticamente con el botón de ordenación de la barra de herramientas de la ventana Propiedades):

    |Propiedad.|Valor|
    |--------------|-----------|
    |**text**|**Buscar por código postal**|
    |**identificador**|`@+id/ZipCodeSearchLabel`|
    |**layout_marginStart**|`10dp`|
    |**textColor**|`@android:color/white`|
    |**textStyle**|`bold`|

    > [!TIP]
    >  Tenga en cuenta que muchas propiedades no contienen una lista desplegable de valores que pueda seleccionar.  Puede resultar difícil saber qué valor de cadena utilizar para cualquier propiedad determinada. Para obtener sugerencias, intente buscar el nombre de una propiedad en la página de la clase [`R.attr`](http://developer.android.com/reference/android/R.attr.html).
    >
    >  Además, una búsqueda rápida en la web conduce generalmente a una página en [http://stackoverflow.com/](http://stackoverflow.com/), donde otras personas han usado la misma propiedad.

     Como referencia, si cambia a la vista **Código fuente**, verá el siguiente código para este elemento:

    ```xml
    <TextView
        android:text="Search by Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/ZipCodeSearchLabel"
        android:layout_marginStart="10dp"
        android:textColor="@android:color/white"
        android:textStyle="bold" />

    ```

7.  Desde el **Cuadro de herramientas**, arrastre un control **TextView** hasta el control **RelativeLayout** y colóquelo debajo del control ZipCodeSearchLabel. Coloque el control nuevo en el borde apropiado del control existente. Es útil acercar el diseñador un poco para colocar el control.

8. En la ventana **Propiedades** , establezca estas propiedades:

    |Propiedad|Valor|
    |--------------|-----------|
    |**texto**|**Código postal**|
    |**identificador**|`@+id/ZipCodeLabel`|
    |**layout_marginStart**|`10dp`|
    |**layout_marginTop**|`6dp`|
    |**textColor**|`@android:color/white`|

    Este es el aspecto que debe tener el código de la vista **Origen**:

    ```xml
    <TextView
        android:text="Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeSearchLabel"
        android:id="@+id/ZipCodeLabel"
        android:layout_marginStart="10dp"
        android:layout_marginTop="6dp"
        android:textColor="@android:color/white" />
    ```

9. Desde el **Cuadro de herramientas**, arrastre un control **Number** hasta **RelativeLayout** y colóquelo debajo de la etiqueta **Código postal**. Después, establezca las siguientes propiedades:

    |Propiedad.|Valor|
    |--------------|-----------|
    |**identificador**|`@+id/zipCodeEntry`|
    |**layout_marginStart**|`10dp`|
    |**layout_marginBottom**|`10dp`|
    |**width**|`165dp`|
    |**textColor**|`@android:color/white`|

    El control **Número** es donde el usuario tendrá que escribir un código postal de Estados Unidos de cinco dígitos. Este es el marcado que corresponde a ese control:

    ```xml
    <EditText
        android:inputType="number"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeLabel"
        android:id="@+id/zipCodeEntry"
        android:layout_marginStart="10dp"
        android:layout_marginBottom="10dp"
        android:width="165dp"
        android:textColor="@android:color/white" />
    ```

10. Desde el **Cuadro de herramientas**, arrastre un **Botón** hasta el control **RelativeLayout** y colóquelo a la derecha del control zipCodeEntry. Después, establezca estas propiedades:

    |Propiedad.|Valor|
    |--------------|-----------|
    |**identificador**|`@+id/weatherBtn`|
    |**texto**|**Obtener el tiempo**|
    |**layout_marginStart**|`20dp`|
    |**layout_alignBottom**|`@id/zipCodeEntry`|
    |**width**|`165dp`|

    ```xml
    <Button
        android:text="Get Weather"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/zipCodeEntry"
        android:id="@+id/weatherBtn"
        android:layout_marginStart="20dp"
        android:layout_alignBottom="@id/zipCodeEntry"
        android:width="165dp" />
    ```

11. Ahora sabe lo suficiente para crear una interfaz de usuario básica con el uso del diseñador de Android. También puede crear una interfaz de usuario si agrega marcado directamente al archivo *Main.axml* de la página. Para crear el resto de la interfaz de usuario de esa manera, cambie a la vista Origen en el diseñador y, a continuación, pegue el marcado siguiente *debajo* de la etiqueta de cierre `</RelativeLayout>`. (Deben estar debajo de la etiqueta porque estos elementos *no* forman parte de `RelativeLayout`).

    ```xml
    <TextView
        android:text="Location"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/locationLabel"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/locationText"
        android:layout_marginStart="20dp"
        android:layout_marginBottom="10dp" />
    <TextView
        android:text="Temperature"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/tempLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/tempText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Wind Speed"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/windLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/windText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Humidity"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/humidtyLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/humidityText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Visibility"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/visibilityLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/visibilityText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Time of Sunrise"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunriseLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunriseText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Time of Sunset"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunsetLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunsetText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    ```

12. Guarde el archivo y cambie a la vista **Diseño**. Su IU aparecerá de la siguiente forma:

     ![IU para aplicaciones Android](../cross-platform/media/xamarin_androidui.png)

13. Abra **MainActivity.cs**. Este es el aspecto que debe tener el código:

    ```csharp
    protected override void OnCreate (Bundle bundle)
    {
        base.OnCreate (bundle);

        // Set our view from the "main" layout resource
        SetContentView (Resource.Layout.Main);
    }
    ```

14. Compile el proyecto Android para comprobar su trabajo. En el proceso de compilación se agregan identificadores de control al archivo *Resource.Designer.cs*, para que pueda hacer referencia a los controles por nombre en código.

### <a name="consume-your-shared-code"></a>Use su código compartido

1.  Abra el archivo *MainActivity.cs* del proyecto **WeatherApp** en el editor de código y reemplace sus contenidos con el siguiente código. Este código llama al método `GetWeather` que usted definió en su código compartido. A continuación, en la IU de la aplicación, se muestra la información que se recupera de ese método.

    ```csharp
    using System;
    using Android.App;
    using Android.Widget;
    using Android.OS;

    namespace WeatherApp.Droid
    {
        [Activity(Label = "Sample Weather App",
                  Theme = "@android:style/Theme.Material.Light",
                  MainLauncher = true)]
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

    Tenga en cuenta que se ha dado a la actividad un tema para un fondo claro.

### <a name="run-the-app-and-see-how-it-looks"></a>Ejecute la aplicación y vea cómo funciona

1.  En el **Explorador de soluciones**, asegúrese de que el proyecto **WeatherApp.Droid** esté establecido como proyecto de inicio.

2.  Seleccione un destino de emulador o un dispositivo adecuado y después presione la tecla F5 para iniciar la aplicación.

    > [!NOTE]
    > Si Visual Studio indica que el proyecto de Android no puede encontrar el archivo Newtonsoft.Json, agregue ese paquete NuGet al proyecto de Android.

3.  En el dispositivo o el emulador, escriba un código postal de cinco dígitos válido de los Estados Unidos en el cuadro de edición y presione **Obtener el tiempo**. Los datos meteorológicos de esa región aparecerán en los controles.

    [![Aplicación Xamarin en Android](../cross-platform/media/cross-plat-xamarin-build-1-android.png)](../cross-platform/media/cross-plat-xamarin-build-1-android-Large.png#lightbox)

> [!TIP]
>  El código fuente completo para este proyecto está en el [repositorio mobile-samples en GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

<a name="Windows" />

## <a name="design-ui-for-windows"></a>Diseñar la interfaz de usuario para Windows

El paso siguiente es diseñar la interfaz de usuario para Windows, conectarla al código compartido y, después, ejecutar la aplicación.

### <a name="design-the-look-and-feel-of-your-app"></a>Diseñe la apariencia y el funcionamiento de su aplicación

 El proceso de diseñar una interfaz de usuario de UWP nativa en una aplicación Xamarin no difiere del de cualquier otra aplicación UWP nativa. Por este motivo, aquí no se va a hablar del uso del diseñador. Para obtener información detallada, consulte [Crear una interfaz de usuario mediante el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 En su lugar, abra *MainPage.xaml* y reemplace todo el contenido XAML por el marcado siguiente:

```xaml
<Page
    x:Class="WeatherApp.UWP.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.UWP"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

        <StackPanel HorizontalAlignment="Left"
                    VerticalAlignment="Top"
                    Height="40" Margin="10,0,0,0" Width="400">
            <TextBlock Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left"
                    VerticalAlignment="Top"
                    Height="120" Margin="10,40,0,0" Width="400"
                    Background="#FF545454">

            <TextBlock Text="Search by Zip Code" TextWrapping="Wrap"
                       HorizontalAlignment="Left" Margin="10,10,0,0"
                       Foreground="White" FontSize="18" FontWeight="Bold" />

            <TextBlock Text="Zip Code" TextWrapping="Wrap"
                       Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>

            <StackPanel Orientation="Horizontal">

                <TextBox x:Name="zipCodeEntry" Text=""
                         Margin="10,10,0,0" VerticalAlignment="Top"
                         InputScope="Number" Width="165" />

                <Button x:Name="weatherBtn" Content="Get Weather"
                        Foreground="White" Width="165" Margin="20,0,0,0" Height="60"
                        Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>

        <StackPanel Margin="10,175,0,0">
            <StackPanel.Resources>
                <Style x:Key="commonText" TargetType="TextBlock">
                    <Setter Property="HorizontalAlignment" Value="Left" />
                    <Setter Property="VerticalAlignment" Value="Top" />
                    <Setter Property="TextWrapping" Value="Wrap" />
                </Style>

                <Style x:Key="labelText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="14" />
                    <Setter Property="Foreground" Value="#FFA8A8A8" />
                </Style>

                <Style x:Key="valueText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="18" />
                    <Setter Property="Margin" Value="10, 0, 0, 10" />
                </Style>
            </StackPanel.Resources>

            <TextBlock Text="Location" Style="{StaticResource labelText}" />
            <TextBlock x:Name="locationText" Style="{StaticResource valueText}" />

            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="tempText" Style="{StaticResource valueText}" />

            <TextBlock Text="Wind Speed" Style="{StaticResource labelText}" />
            <TextBlock x:Name="windText" Style="{StaticResource valueText}" />

            <TextBlock Text="Humidity" Style="{StaticResource labelText}" />
            <TextBlock x:Name="humidityText" Style="{StaticResource valueText}" />

            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="visibilityText" Style="{StaticResource valueText}" />

            <TextBlock Text="Time of Sunrise" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunriseText" Style="{StaticResource valueText}" />

            <TextBlock Text="Time of Sunset" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunsetText" Style="{StaticResource valueText}" />
        </StackPanel>
    </Grid>
</Page>
```

### <a name="consume-your-shared-code"></a>Use su código compartido

En el archivo de código subyacente *MainPage.xaml.cs*, agregue el siguiente controlador de eventos para el botón:

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

Este código llama al método `GetWeather` que usted definió en su código compartido. `GetWeather` es el mismo método al que llamó en su aplicación de Android. Además, este código muestra los datos recuperados de ese método en los controles de la IU de su aplicación.

### <a name="run-the-app-and-see-how-it-looks"></a>Ejecute la aplicación y vea cómo funciona

1.  En el **Explorador de soluciones**, establezca el proyecto **WeatherApp.UWP** como el proyecto de inicio.

2.  En el cuadro desplegable **Plataformas de soluciones**, seleccione **x86** y, después, **Equipo local** para implementar la aplicación en el escritorio de Windows 10.

3.  Inicie la aplicación con la tecla **F5**.

4.  Escriba un código postal de Estados Unidos de cinco dígitos válido en el cuadro de edición y presione **Obtener el tiempo**. A continuación, los datos meteorológicos de esa región aparecen en la página.

    [![Aplicación Xamarin en UWP](../cross-platform/media/cross-plat-xamarin-build-1-uwp.png)](../cross-platform/media/cross-plat-xamarin-build-1-uwp-Large.png#lightbox)

> [!TIP]
>  El código fuente completo para este proyecto está en el [repositorio mobile-samples en GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

<a name="next" />

## <a name="next-steps"></a>Pasos siguientes

 **Agregar la interfaz de usuario para iOS a la solución**

 Amplíe este ejemplo agregando una interfaz e usuario nativa para iOS. Para probar el código en iOS, tendrá que conectarse a un equipo Mac en la red local que tenga instalados Xcode y Xamarin. Después, puede usar el diseñador de iOS directamente en Visual Studio. Vea el [repositorio mobile-samples en GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather) para obtener una aplicación completa.

 Consulte también el tutorial [Hello, iOS](/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?tabs=vswin).

 **Agregar código específico de la plataforma en el proyecto compartido**

 El código compartido en una biblioteca de .NET Standard es independiente de la plataforma. La biblioteca se compila una vez y se incluye en cada paquete de aplicación específico de la plataforma. Si quiere escribir código compartido que use la compilación condicional para aislar el código específico de la plataforma, puede usar un proyecto *compartido*. Para más información, consulte [Opciones de uso compartido del código](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/practical-code-sharing-strategies).

## <a name="see-also"></a>Vea también

- [Documentación de Xamarin](http://docs.microsoft.com/xamarin)
- [Centro de desarrollo de Windows](https://dev.windows.com/en-us)
- [Póster de referencia rápida de Swift y C#](http://aka.ms/scposter)
