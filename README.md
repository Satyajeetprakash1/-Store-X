# Store-X
# Store-X: Modern E-Commerce Reference Application

A scalable, modular, and AI-enhanced e-commerce web application inspired by .NET Aspire architecture.

---

## 🚀 Getting Started

This version of **Store-X** is built using **.NET 9**, and follows a microservices-based structure.

---

## ✅ Prerequisites

* Clone this repository: [https://github.com/Satyajeetprakash1/Store-X](https://github.com/Satyajeetprakash1/Store-X)
* [Install & start Docker Desktop](https://docs.docker.com/engine/install/)

### Windows with Visual Studio

* Install [Visual Studio 2022 version 17.10 or newer](https://visualstudio.microsoft.com/vs/).

  * Select the following workloads:

    * `ASP.NET and web development`
    * `.NET Aspire SDK` (from Individual Components)
    * Optional: `.NET MAUI` if you're using client apps

#### Or, run the script:

```powershell
install-Module -Name Microsoft.WinGet.Configuration -AllowPrerelease -AcceptLicense -Force
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
get-WinGetConfiguration -file .\.configurations\vside.dsc.yaml | Invoke-WinGetConfiguration -AcceptConfigurationAgreements
```

### macOS / Linux / VS Code

* Install the latest [.NET 9 SDK](https://dot.net/download)
* Optional: Install [VS Code + C# Dev Kit](https://code.visualstudio.com/docs/csharp/get-started)

Or run:

```powershell
install-Module -Name Microsoft.WinGet.Configuration -AllowPrerelease -AcceptLicense -Force
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
get-WinGetConfiguration -file .\.configurations\vscode.dsc.yaml | Invoke-WinGetConfiguration -AcceptConfigurationAgreements
```

> Note: You may need `sudo` for some commands.

---

## ▶️ Running Store-X

Make sure **Docker Desktop** is running.

### Option 1: From Visual Studio (Windows)

* Open `StoreX.Web.slnf`
* Set `StoreX.AppHost.csproj` as the startup project
* Hit `Ctrl + F5` to launch Aspire dashboard

### Option 2: From Terminal

```sh
dotnet run --project src/StoreX.AppHost/StoreX.AppHost.csproj
```

Look for output like:

```
Login to the dashboard at: http://localhost:19888/login?t=your-token
```

> If needed, install HTTPS dev certs via: `dotnet dev-certs https --trust`

---

## 🤖 AI Integration

To use Azure OpenAI, modify `StoreX.AppHost/appsettings.json`:

```json
"ConnectionStrings": {
  "OpenAi": "Endpoint=xxx;Key=xxx;"
}
```

In `Program.cs`, set:

```csharp
bool useOpenAI = true;
```

Refer to [Azure OpenAI Aspire Docs](https://learn.microsoft.com/dotnet/aspire/azureai/azureai-openai-component?tabs=dotnet-cli)

---

## ☁️ Deploying with Azure Developer CLI (azd)

* Install [Azure Developer CLI](https://aka.ms/azd)
* Log in:

```sh
azd auth login
```

* From project root:

```sh
azd init
azd up
```

* During init:

  * Choose ".NET Aspire"
  * Expose `webapp`
  * Give your environment a name

Once deployed, the CLI will show the app's URL. You can re-deploy changes using:

```sh
azd up
```

---

## 📦 Sample Data

All catalog data (names, descriptions, prices) are located in:
[store-catalog.json](src/Catalog.API/Setup/store-catalog.json)

Images and text are AI-generated using:

* ✍️ [GPT-4 Turbo](https://openai.com/gpt-4)
* 🖼️ [DALL·E 3](https://openai.com/dall-e-3)


---

## 📄 License

This project is licensed under the Apache License 2.0 License - see the [LICENSE](LICENSE) file for details.
