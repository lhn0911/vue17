<template>
  <div>
    <h1>Admin Dashboard</h1>
    <nav>
      <ul>
        <li>
          <router-link to="/admin/manager-user">User Management</router-link>
        </li>
        <li>
          <router-link to="/admin/manager-product"
            >Product Management</router-link
          >
        </li>
        <li><router-link to="/admin/settings">Settings</router-link></li>
      </ul>
    </nav>
    <router-view />
    <!-- Nơi hiển thị các route con -->
  </div>
</template>
  
  <script>
export default {
  name: "Admin",
};
</script>
  
  <style scoped>
nav ul {
  list-style-type: none;
}
nav ul li {
  display: inline;
  margin-right: 15px;
}
</style>
  