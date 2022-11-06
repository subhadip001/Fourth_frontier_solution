 <template>
  <div id="app">
    <p><strong>Add a new contact:</strong></p>
    <div>
      <form @submit="formSubmit">
        <label
          >First Name:
          <input type="text" value="Coder" name="fname" class="userFirstname"
        /></label>
        <br />
        <label
          >Last Name:
          <input type="text" value="Byte" name="lname" class="userLastname"
        /></label>
        <br />
        <label
          >Phone:
          <input
            type="number"
            value="8885559999"
            name="phone"
            class="userPhone"
        /></label>
        <br />
        <button class="submitButton">Add New Contact</button>
      </form>
    </div>

    <!-- items should go here -->
    <!-- {{ items.map((item , id) => { return
    item.fname
     }) 
    }} -->
    <div>
      {{ items.map((item) => item) }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [],
    };
  },
  methods: {
    formSubmit(e) {
      const form = document.querySelector("form");
      e.preventDefault();

      const first = form.elements.namedItem("fname").value;
      const last = form.elements.namedItem("lname").value;
      const ph = form.elements.namedItem("phone").value;
      this.items.push({
        fname: first,
        lname: last,
        phone: ph,
      });
      function compare(a, b) {
        if (a.lname < b.lname) {
          return -1;
        }
        if (a.lname > b.lname) {
          return 1;
        }
        return 0;
      }

      this.items.sort(compare);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
