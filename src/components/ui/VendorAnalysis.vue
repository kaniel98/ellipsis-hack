<template>
  <div class="container">
    <div class="row">
      <h1>Vendor Analysis</h1>
      <input
        type="text"
        class="form-control bg-light text-dark rounded-1 border-0 my-4"
        placeholder="Search Vendor"
        @keyup="searchVendor()"
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
            <td
              :class="[
                vendor.conversion_rate > 0
                  ? 'text-success'
                  : 'text-danger',
              ]"
            >
              {{ vendor.conversion_rate }} %
            </td>
            <td
              :class="[
                vendor.customer_retention_rate > 0
                  ? 'text-success'
                  : 'text-danger',
              ]"
            >
              {{ vendor.customer_retention_rate }} %
            </td>
            <td
              :class="[
                vendor.average_order_rate > 0
                  ? 'text-success'
                  : 'text-danger',
              ]"
            >
              {{ vendor.average_order_rate }} %
            </td>
            <td
              :class="[
                vendor.net_profit_rate > 0
                  ? 'text-success'
                  : 'text-danger',
              ]"
            >
              {{ vendor.net_profit_rate }} %
            </td>
            <td
              :class="[
                vendor.cart_abandonment_rate > 0
                  ? 'text-success'
                  : 'text-danger',
              ]"
            >
              {{ vendor.cart_abandonment_rate }} %
            </td>
            <td>{{ vendor.number_of_orders }} </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "VendorAnalysis",
  data() {
    return {
      vendors: [],
      filteredVendors: [],
      titles: ["id", "Vendor", "Conversion Rate", "Customer Retention Rate", "Average Order Rate", "Net Profit Rate", "Cart Abandonment Rate", "Number of Orders"],
      textSearch: "",
    };
  },
  async mounted() {
    const res = await fetch("./dummy.json");
    const data = await res.json();
    console.log(data);
    this.vendors = data;
    this.filteredVendors = data;
  },
  methods: {
    searchVendor() {
      this.filteredVendors = this.vendors.filter(
        (vendor) =>
          vendor.name.toLowerCase().includes(this.textSearch.toLowerCase()) ||
          vendor.symbol.toLowerCase().includes(this.textSearch.toLowerCase())
      );
    },
  },
};
</script>