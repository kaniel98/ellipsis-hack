<template>
    <div class="container">
        <div class="row">
            <p class="display-4">Vendor Analysis</p>
            <input
                type="text"
                class="form-control bg-light text-dark rounded-1 border-0 my-4"
                placeholder="Search Vendor"
                @keyup.enter="searchVendor()"
                v-model="textSearch"
            />
            <table class="table table-light">
                <thead>
                    <tr>
                        <th v-for="title in titles" :key="title">{{ title }}</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(vendor, index) in filteredVendors" :key="vendor.id">
                        <td class="text-muted">{{ index + 1 }}</td>
                        <td>
                            <!-- <img :src="vendor.image" style="width: 2rem" class="me-3" /> -->
                            <span>
                                {{ vendor.name }}
                            </span>
                        </td>
                        <td :class="[vendor.conversion_rate > 0 ? 'text-success' : 'text-danger']">{{ vendor.conversion_rate }} %</td>
                        <td :class="[vendor.customer_retention_rate > 0 ? 'text-success' : 'text-danger']">{{ vendor.customer_retention_rate }} %</td>
                        <td :class="[vendor.average_order_rate > 0 ? 'text-success' : 'text-danger']">{{ vendor.average_order_rate }} %</td>
                        <td :class="[vendor.net_profit_rate > 0 ? 'text-success' : 'text-danger']">{{ vendor.net_profit_rate }} %</td>
                        <td :class="[vendor.cart_abandonment_rate > 0 ? 'text-success' : 'text-danger']">{{ vendor.cart_abandonment_rate }} %</td>
                        <td>{{ vendor.number_of_orders }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
import vendors from './dummy.json';

export default {
    name: 'VendorAnalysis',
    data() {
        return {
            vendors: vendors.vendors,
            filteredVendors: vendors.vendors,
            titles: [
                'id',
                'Vendor',
                'Conversion Rate',
                'Customer Retention Rate',
                'Average Order Rate',
                'Net Profit Rate',
                'Cart Abandonment Rate',
                'Number of Orders'
            ],
            textSearch: ''
        };
    },

    methods: {
        searchVendor() {
            const searchValue = this.textSearch.toLowerCase();

            if (this.searchValue === '') {
                return;
            }

            let tempArray = [];
            for (const vendor of this.vendors) {
                if (vendor.name.toLowerCase().includes(searchValue)) {
                    tempArray.push(vendor);
                }
            }
            this.filteredVendors = tempArray;
        }
    }
};
</script>
