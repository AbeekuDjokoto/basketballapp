<template>
  <a
    class="btn btn-primary mb-5"
    data-bs-toggle="offcanvas"
    href="#offcanvasExample"
    role="button"
    aria-controls="offcanvasExample"
    @click="getPatient"
  >
    Toggle User Info
  </a>
 
  <table class="table mt-5 caption-top">
    <caption style="border: inherit; background-color: lightgrey">
      <span class="text-center text-uppercase"
        ><strong>Blood Glucouse Log Sheet/Quantities of food</strong></span
      >
    </caption>
    <thead>
      <tr>
        <th scope="col">Number</th>
        <th scope="col">Fasting Blood Glucose</th>
        <th scope="col">Breakfast + Quantities</th>
        <th scope="col">2 hours Breakfast</th>
        <th scope="col">Lunch Quantities</th>
        <th scope="col">2 hours after lunch</th>
        <th scope="col">Supposed Quantities</th>
        <th scope="col">2 hours after supper</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(person, index) in personDetails" :key="person">
        <td>{{ index + 1 }}</td>
        <td>{{ person.fasting }}</td>
        <td>{{ person.breakfast }}</td>
        <td>{{ person.break }}</td>
        <td>{{ person.lunch }}</td>
        <td>{{ person.afterLunch }}</td>
        <td>{{ person.quantities }}</td>
        <td>{{ person.supper }}</td>
      </tr>
    </tbody>
  </table>

  <div
    class="offcanvas offcanvas-start"
    tabindex="-1"
    id="offcanvasExample"
    aria-labelledby="offcanvasExampleLabel"
  >
    <div class="offcanvas-header">
      <h5 class="offcanvas-title" id="offcanvasExampleLabel">
        {{ personDetails.name }}
      </h5>
      <button
        type="button"
        class="btn-close"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body">
      <div>This is the profile of the patient</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
        personName: null,
      personDetails: [
        {
          name: null,
          fasting: "true",
          breakfast: "indomie, 250mg",
          break: "timeout",
          lunch: "banku, 18mg",
          afterLunch: "tea",
          quantities: "30mg",
          supper: "tea",
        },
        {
          name: null,
          fasting: "false",
          breakfast: "rice, 50mg",
          break: "timeout",
          lunch: "",
          afterLunch: "tea",
          quantities: "20mg",
          supper: "oats",
        },
        {
          name: null,
          fasting: "true",
          breakfast: "banku, 20mg",
          break: "timeout",
          lunch: "tea, 8mg",
          afterLunch: "tea",
          quantities: "50mg",
          supper: "coffee",
        },
        {
          name: null,
          fasting: "false",
          breakfast: "indomie, 80mg",
          break: "timeout",
          lunch: "banku, 18mg",
          afterLunch: "",
          quantities: "10mg",
          supper: "bread and egg",
        },
        {
          name: null,
          fasting: "true",
          breakfast: "kenkey, 10mg",
          break: "timeout",
          lunch: "",
          afterLunch: "tea",
          quantities: "550mg",
          supper: "tea",
        },
        {
          name: null,
          fasting: "true",
          breakfast: "indomie, 90mg",
          break: "timeout",
          lunch: "banku, 18mg",
          afterLunch: "",
          quantities: "550mg",
          supper: "tea",
        },
        {
          name: null,
          fasting: "false",
          breakfast: "jollof, 50mg",
          break: "timeout",
          lunch: "rice, 18mg",
          afterLunch: "",
          quantities: "550mg",
          supper: "bread and egg",
        },
        {
          name: null,
          fasting: "true",
          breakfast: "indomie, 230mg",
          break: "timeout",
          lunch: "",
          afterLunch: "tea",
          quantities: "550mg",
          supper: "sausage",
        },
        {
          name: null,
          fasting: "true",
          breakfast: "ice kenkey, 50mg",
          break: "timeout",
          lunch: "banku, 18mg",
          afterLunch: "",
          quantities: "50mg",
          supper: "coffee",
        },
      ],
    };
  },
  computed: {
    check(){
        this.personName = localStorage.getItem("patientName")
        console.log(this.personName)
        return this.personName
    }
  },
  methods: {
    getPatient() {
      if (localStorage["patientName"] == undefined) {
        console.log(localStorage.getItem("patientName"));
      } else if (localStorage["doctorName"] == undefined) {
        console.log(localStorage.getItem("doctorName"));
      } else if (localStorage["patientName"]) {
        this.personDetails.name = localStorage.getItem("patientName");
        return this.personDetails.name;
      } else if (localStorage["doctorName"]) {
        this.personDetails.name = localStorage.getItem("doctorName");
        return this.personDetails.name;
      }

      console.log(this.personDetails.name);
    },
  },
};
</script>

<style></style>
