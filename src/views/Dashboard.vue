<template>
  <div class="container-fluid ">
    <div class="row">
      <div
        class="sidebar col-lg-4 col-md-4 bg-success"
        style="height: 100vh"
      >
      <div class="justify-content-start align-items-center d-flex mt-2">
        <span class="material-symbols-outlined"> dashboard </span>
        <span class="fw-light">Dashboard</span>
      </div>
        
        <h1 class="fw-light mb-5 mt-3">Welcome {{ doctorName }}</h1>
        <div class="d-grid gap-2 col-6 mx-auto">
         <router-link to="/"><button class="btn btn-outline-dark mt-5" style= "width: 100%" type="button">Log out</button></router-link> 
        </div>
      </div>

      <div class="col-md-8 col-lg-8" >
        <table class="table mt-5 mx-2 caption-top" style="width: 100%" v-if="patientStatus == true">
          <caption style="border: inherit; background-color: lightgrey">
            <span class="text-center text-uppercase"
              ><strong
                >Blood Glucouse Log Sheet/Quantities of food</strong
              ></span
            >
          </caption>
          <thead>
            <tr>
              <th scope="col">Number</th>
              <th scope="col">Breakfast Quant</th>
              <th scope="col">2 hours Breakfast</th>
              <th scope="col">Lunch Quant</th>
              <th scope="col">2 hours after lunch</th>
              <th scope="col">Supposed Quant</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(person, index) in returnfiltered" :key="person">
              <td>{{ index + 1 }}</td>
              <td>{{ person.breakfast }}</td>
              <td>{{ person.break }}</td>
              <td>{{ person.lunch }}</td>
              <td>{{ person.afterLunch }}</td>
              <td>{{ person.quantities }}</td>
            </tr>
          </tbody>
        </table>

        <div v-else>
          <h1 class="font-monospace d-flex">
            Patient Information
          </h1>

          <div
            class="card"
            style="width: 22rem"
            v-if="doctorStatus == true"
          >
            <img
              src="../assets/PatientCare.svg.png"
              class="card-img-top"
              alt="..."
            />
            <div class="card-body">
              <h5 class="card-title fw-bold">Patient Information</h5>
              <p class="card-text font-monospace">Fact check</p>
            </div>
            <ul class="list-group list-group-flush">
              <li
                class="list-group-item font-monospace"
                style="
                  background: linear-gradient(
                    246.26deg,
                    #585dfe 0%,
                    #fb3796 100%
                  );
                "
              >
                Total Number of Patients: {{ personDetails.length }}
              </li>
              <li class="list-group-item font-monospace">
                Patient's attended to: {{ attendedTo.length }}
              </li>
              <li class="list-group-item font-monospace">
                Patient's unatended to: {{ notAttendedTo.length }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      doctorName: "",
      personName: null,
      patientStatus: false,
      doctorStatus: false,
      personDetails: [
        {
          name: "Abeeku",
          fasting: "true",
          breakfast: "indomie, 250mg",
          break: "timeout",
          lunch: "banku, 18mg",
          afterLunch: "tea",
          quantities: "30mg",
          supper: "tea",
          attendedTo: true,
        },
        {
          name: "Winnifred",
          fasting: "false",
          breakfast: "rice, 50mg",
          break: "timeout",
          lunch: "",
          afterLunch: "tea",
          quantities: "20mg",
          supper: "oats",
          attendedTo: true,
        },
        {
          name: "fred",
          fasting: "true",
          breakfast: "banku, 20mg",
          break: "timeout",
          lunch: "tea, 8mg",
          afterLunch: "tea",
          quantities: "50mg",
          supper: "coffee",
          attendedTo: false,
        },
        {
          name: "kwabena",
          fasting: "false",
          breakfast: "indomie, 80mg",
          break: "timeout",
          lunch: "banku, 18mg",
          afterLunch: "",
          quantities: "10mg",
          supper: "bread and egg",
          attendedTo: false,
        },
        {
          name: "charles",
          fasting: "true",
          breakfast: "kenkey, 10mg",
          break: "timeout",
          lunch: "",
          afterLunch: "tea",
          quantities: "550mg",
          supper: "tea",
          attendedTo: true,
        },
        {
          name: "alex",
          fasting: "true",
          breakfast: "indomie, 90mg",
          break: "timeout",
          lunch: "banku, 18mg",
          afterLunch: "",
          quantities: "550mg",
          supper: "tea",
          attendedTo: true,
        },
        {
          name: "george",
          fasting: "false",
          breakfast: "jollof, 50mg",
          break: "timeout",
          lunch: "rice, 18mg",
          afterLunch: "",
          quantities: "550mg",
          supper: "bread and egg",
          attendedTo: false,
        },
        {
          name: "anderson",
          fasting: "true",
          breakfast: "indomie, 230mg",
          break: "timeout",
          lunch: "",
          afterLunch: "tea",
          quantities: "550mg",
          supper: "sausage",
        },
        {
          name: "prince",
          fasting: "true",
          breakfast: "ice kenkey, 50mg",
          break: "timeout",
          lunch: "banku, 18mg",
          afterLunch: "",
          quantities: "50mg",
          supper: "coffee",
          attendedTo: true,
        },
      ],
    };
  },
  created() {
    this.check();
  },
  computed: {
    returnfiltered() {
      return this.personDetails.filter((name) => {
        return name.name === localStorage.getItem("patientName");
      });
    },
    attendedTo() {
      return this.personDetails.filter((person) => {
        return person.attendedTo === true;
      });
    },
    notAttendedTo() {
      return this.personDetails.filter((person) => {
        return person.attendedTo === false;
      });
    },
  },
  methods: {
    getPatient() {
      if (localStorage["patientName"]) {
        this.personDetails.name = localStorage.getItem("patientName");
        console.log(this.personDetails.name);
        // return this.personDetails.name;
      } else {
        this.doctorName = localStorage.getItem("doctorName");
        console.log(this.doctorName);
        // return this.personDetails.name;
      }

      console.log(this.personDetails.name);
    },
    check() {
      if (localStorage["patientName"]) {
        this.doctorName = localStorage.getItem("patientName");
        this.patientStatus = true;
      } else {
        this.doctorName = localStorage.getItem("doctorName");
        this.doctorStatus = true;
        this.patientStatus = false;
      }
    },
    doctorInfo() {
      if (localStorage["patientName"]) {
        this.patientStatus = true;
      } else {
        this.patientStatus = false;
      }
      this.personDetails;
    },
  },
};
</script>

<style></style>
