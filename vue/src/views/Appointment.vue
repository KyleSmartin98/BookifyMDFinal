<template>
  <div class="appointment-container">
    <div class="appointment-photo-array">
      <img class="ap-p" src="../assets/appointments-1.png" alt="Appointment Photo 1">
      <img class="ap-p" src="../assets/appointments-2.png" alt="Appointment Photo 2">
      <img src="../assets/appointments-3.png" alt="Appointment Photo 3">
    </div>
      
    <h1>Appointments</h1>
  
  <section class="appointment-body elevated-box">  
    
    <doctor-schedule v-if="this.currentUserType"/>

    <patient-appointments v-if="!this.currentUserType"/>

  </section>

  </div>
</template>

<script>
import DoctorSchedule from '../components/DoctorSchedule.vue';
import PatientAppointments from '../components/PatientAppointments.vue';

export default {
  components: { DoctorSchedule, PatientAppointments },
  data() {
      return {
        user: {
          //role: "doctor"
          role: "patient"
        }
      }
    },
    computed:{
        currentUser(){
            return this.$store.state.user
            },
        currentUserType(){
            return this.$store.state.profileType.isDoctor;
        },
        currentUserProfile(){
            return this.$store.state.profile;
        },
    },
}

</script>

<style>
.appointment-container{
    margin-top: 184px;
    align-content: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: start space-between;
    padding-bottom: 3%;
    z-index: 1;
    min-height: calc(100vh - 148px);
   }
.appointment-body{
    margin: 20px 0 0px 20px;
    font-size: 1.1rem;
   }
.ap-p{
margin-right: 20px;
}
.appointment-photo-array{
  padding-top: 2%;
}
</style>
