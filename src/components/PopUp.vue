<template>
  <div>
    <div v-if="isVisible" id="alert-box" class="alert-box">
      <p>{{ alertMessage }}</p>
      <button class="close-button" @click="closeAlert">✖</button>
    </div>
  </div>
</template>

<script>
import confetti from 'canvas-confetti';

export default {
  data() {
    return {
      isVisible: false,
      alertMessage: '',
      alertMessages: [],
      currentAlertIndex: 0,
      timeoutId: null,
      alertSchedule: [
        { min: 30000, max: 50000 }, // Random between 30-50 seconds
        40000,                      // 40 seconds after the first alert
        10000,                      // 10 seconds after the second alert
        80000,                      // 1 minute 20 seconds after the third alert
        120000                      // 2 minutes after the fourth alert
      ],
      alertIndex: 0,
    };
  },
  created() {
    this.generateAlertMessages();
    this.scheduleNextAlert(); // Schedule the first alert
  },
  beforeUnmount() {
    clearTimeout(this.timeoutId);
  },
  methods: {
    generateAlertMessages() {
      const funnyNames = [
        "Bonk", "Pok", "Paki", "Shark", "Fluff", "Wobble", "Doodle", "Zonk", "Fizz", "Giggles",
        "OlenMoist", "KiliJaner", "JeoBiden", "Bezosaurus", "MarsZucker", "RihannaGold", 
        "NickiCoins", "CardiBlockchain", "GagaEther", "MadonnaMiner", "TSwiftCrypto", 
        "AdeleAssets", "SnoopDogecoin", "MuskMartian", "BuffettBits", "ZuckZillions", 
        "BransonBlocks", "RogenReserve", "StreepSatoshis", "OprahOrbs"
      ];

      for (let i = 1; i <= 100; i++) {
        const address = this.getRandomString(4) + '...' + this.getRandomString(3);
        const funnyName = funnyNames[Math.floor(Math.random() * funnyNames.length)];
        this.alertMessages.push(`${address} created $${funnyName}`);
      }
    },
    getRandomString(length) {
      const characters = '0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz';
      let result = '';
      for (let i = 0; i < length; i++) {
        result += characters[Math.floor(Math.random() * characters.length)];
      }
      return result;
    },
    showAlert() {
      this.alertMessage = this.alertMessages[this.currentAlertIndex];
      this.isVisible = true;

      // Trigger confetti effect
      this.triggerConfetti();

      setTimeout(this.closeAlert, 6000);

      this.currentAlertIndex = (this.currentAlertIndex + 1) % this.alertMessages.length;

      // Schedule the next alert based on the alert schedule
      this.scheduleNextAlert();
    },
    closeAlert() {
      this.isVisible = false;
    },
    scheduleNextAlert() {
      let delay;
      if (this.alertIndex < this.alertSchedule.length) {
        const schedule = this.alertSchedule[this.alertIndex];
        if (typeof schedule === 'object') {
          delay = Math.random() * (schedule.max - schedule.min) + schedule.min;
        } else {
          delay = schedule;
        }
      } else {
        // Subsequent alerts after the 5th
        delay = 120000 + Math.random() * (40000 - 10000) + 10000; // 2 minutes plus 10-40 seconds
      }

      this.timeoutId = setTimeout(this.showAlert, delay);
      this.alertIndex++;
    },
    triggerConfetti() {
      confetti({
        particleCount: 50,
        spread: 20,
        origin: { x: 0.9, y: 0.9 } // Adjust the confetti origin to just above the pop-up
      });
    }
  }
};
</script>

<style scoped>
/* Alert box container */
.alert-box {
  position: fixed;
  bottom: 20px;
  right: 20px;
  border-radius: 13px;
  background-color: white;
  padding: 20px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
  z-index: 1000;
  animation: pulse 1s ease-out;
}

/* Close button */
.close-button {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  font-size: 16px;
  cursor: pointer;
}

/* Impulse wave effect */
@keyframes pulse {
  0% {
    transform: scale(0.95);
    opacity: 0.7;
  }
  20% {
    transform: scale(1.1);
    opacity: 1;
  }
  40% {
    transform: scale(0.9);
    opacity: 1;
  }
  60% {
    transform: scale(1.05);
    opacity: 1;
  }
  80% {
    transform: scale(0.98);
    opacity: 1;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

p {
  margin-right: 10px;
}
</style>
