<script>
export default {
  methods: {
    async requestGet(url) {
      try {
        const response = await this.$axios.get(url);
        return response.data;
      } catch (error) {
        this.$swal({
          title: "Error",
          text: error.response.data.msg,
          icon: "error",
        });
        return null;
      }
    },
  },
};
</script>
