## Usage

### Basic usage
```csharp
using SdkRindegastos;
using SdkRindegastos.Services;
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace pruebaSdkRindegastos
{
    public partial class Form1 : Form
    {
        private string Token = "here goes the token...";
        public Form1()
        {
            InitializeComponent();
        }

        private async void button1_Click(object sender, EventArgs e)
        {
            //Ejecuto todo el SDK completo
            var rg = new Rindegastos(Token);
            Dictionary<String, String> paramsGetExpenses = new Dictionary<String,String>();
            paramsGetExpenses.Add("Since", "2017-10-01");
            paramsGetExpenses.Add("Until", "2017-10-26");
            paramsGetExpenses.Add("Currency", "CLP");
            paramsGetExpenses.Add("Status", "1");
            paramsGetExpenses.Add("Category", "");
            paramsGetExpenses.Add("ReportId", "");
            paramsGetExpenses.Add("ExpensePolicyId", "");
            paramsGetExpenses.Add("IntegrationStatus", "");
            paramsGetExpenses.Add("IntegrationCode", "");
            paramsGetExpenses.Add("IntegrationDate", "");
            paramsGetExpenses.Add("UserId", "");
            paramsGetExpenses.Add("OrderBy", "");
            paramsGetExpenses.Add("Order", "");
            paramsGetExpenses.Add("ResultsPerPage", "");
            paramsGetExpenses.Add("Page", "");
            var u = await rg.Expenses.getExpenses(paramsGetExpenses);

            //Ejecuto el servicio independiente
            var x = new ExpensesServices(Token);
            var u2 = await x.getExpenses(paramsGetExpenses);
        }
    }
}
```

