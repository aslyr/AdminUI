﻿<div>
    <div class="form-horizontal">
        <div class="form-group">
            <label for="inputEmail3" class="col-sm-2 control-label">CustomerID</label>
            <div class="col-sm-6">
                <input type="text" readonly class="form-control" :value="GetDetail.result.item.CustomerID">
            </div>
        </div>

        <div class="form-group">
            <label for="inputEmail3" class="col-sm-2 control-label">CompanyName</label>
            <div class="col-sm-6">
                <input type="text" class="form-control" :value="GetDetail.result.item.CompanyName">
            </div>
        </div>

        <div class="form-group">
            <label for="inputEmail3" class="col-sm-2 control-label">ContactName</label>
            <div class="col-sm-6">
                <input type="text" class="form-control" :value="GetDetail.result.item.ContactName">
            </div>
        </div>

        <div class="form-group">
            <label for="inputEmail3" class="col-sm-2 control-label">ContactTitle</label>
            <div class="col-sm-6">
                <input type="text" class="form-control" :value="GetDetail.result.item.ContactTitle">
            </div>
        </div>

        <div class="form-group">
            <label for="inputEmail3" class="col-sm-2 control-label">Address</label>
            <div class="col-sm-6">
                <input type="text" class="form-control" :value="GetDetail.result.item.Address">
            </div>
        </div>

        <div class="form-group">
            <label for="inputEmail3" class="col-sm-2 control-label">City</label>
            <div class="col-sm-6">
                <input type="text" class="form-control" :value="GetDetail.result.item.City">
            </div>
        </div>

        <div class="form-group">
            <label for="inputEmail3" class="col-sm-2 control-label">PostalCode</label>
            <div class="col-sm-6">
                <input type="text" class="form-control" :value="GetDetail.result.item.PostalCode">
            </div>
        </div>
        <div class="form-group">
            <label for="inputEmail3" class="col-sm-2 control-label">Country</label>
            <div class="col-sm-6">
                <input type="text" class="form-control" :value="GetDetail.result.item.Country">
            </div>
        </div>
        <div class="form-group">
            <label for="inputEmail3" class="col-sm-2 control-label">Phone</label>
            <div class="col-sm-6">
                <input type="text" class="form-control" :value="GetDetail.result.item.Phone">
            </div>
        </div>

    </div>

    <table class="table">
        <thead>
            <tr>
                <th>OrderID</th>

                <th>Employee</th>
                <th>OrderDate</th>
                <th>RequiredDate</th>
                <th>ShipCountry</th>
                <th>ShipCity</th>
                <th>ShipAddress</th>
                <th>RequiredDate</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="item in GetDetail.result.orders.items">
                <td>{{item.OrderID}}</td>

                <td>{{item.Employee.FirstName}} {{item.Employee.LastName}}</td>
                <td>{{item.OrderDate}}</td>
                <td>{{item.RequiredDate}}</td>
                <td>{{item.ShipCountry}}</td>
                <td>{{item.ShipCity}}</td>
                <td>{{item.ShipAddress}}</td>
                <td>{{item.ShipAddress}}</td>
            </tr>
        </tbody>
    </table>
</div>
<script>
    {
        props: ["token"],
            data: function () {
                return {
                    employeeid: this.token.id,
                    GetDetail: new beetlexAction("/GetCustomerDetail", { id: 0 }, { item: {}, orders: [] }),
                }
            },
        methods: {

        },
        watch: {
            token(val) {
                this.employeeid = val.id;
                this.GetDetail.get({ id: val.id });
            }
        },
        mounted: function () {
            this.GetDetail.get({ id: this.token.id });
        }
    }
</script>