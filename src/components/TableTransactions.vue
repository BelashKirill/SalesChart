<template>
  <table cellspacing="0" class="table-tr">
    <thead>
      <tr>
        <td>TRANSACTION</td>
        <td>DATE & TIME</td>
        <td>AMOUNT</td>
        <td>STATUS</td>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(item, i) in tableData" :key="i">
        <td>
          {{ item.transaction }} <span class="text-bold">{{ item.target }}</span>
        </td>
        <td class="date-cell">{{ item.date }}</td>
        <td>
          <span class="text-lowbold">${{ item.amount }}</span>
        </td>
        <td>
          <span class="badge" :class="'badge-' + item.typeStatus">{{ item.status }}</span>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: "TableTransactions",
  data() {
    return {
      tableData: [
        {
          transaction: "Payment from",
          target: "Bonnie Green",
          date: "Apr 23 ,2021",
          amount: 2300,
          status: "Completed",
          typeStatus: "success",
        },
        {
          transaction: "Payment from",
          target: "Bonnie Green",
          date: "Apr 23 ,2021",
          amount: 2300,
          status: "Completed",
          typeStatus: "success",
        },
        {
          transaction: "Payment failed from",
          target: "Bonnie Green",
          date: "Apr 23 ,2021",
          amount: 2300,
          status: "Cancelled",
          typeStatus: "danger",
        },
        {
          transaction: "Payment from",
          target: "Bonnie Green",
          date: "Apr 23 ,2021",
          amount: 2300,
          status: "Completed",
          typeStatus: "success",
        },
        {
          transaction: "Payment from",
          target: "Bonnie Green",
          date: "Apr 23 ,2021",
          amount: 2300,
          status: "In progress",
          typeStatus: "info",
        },
        {
          transaction: "Payment from",
          target: "Bonnie Green",
          date: "Apr 23 ,2021",
          amount: 2300,
          status: "Completed",
          typeStatus: "success",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
table {
  width: 100%;

  thead {
    tr {
      td {
        padding: 11px 16px;
        font-weight: 600;
        font-size: 12px;
        color: #6b7280;
        text-transform: uppercase;
        background: #f9fafb;
        border-bottom: 1px solid #e5e7eb;

        &:first-child {
          width: 269px;
          border-radius: 12px 0px 0px 0px;
        }

        &:last-child {
          width: 254px;
          border-radius: 0px 12px 0px 0px;
        }

        &:nth-child(2) {
          width: 357px;
        }

        &:nth-child(3) {
          width: 405px;
        }
      }
    }
  }

  tbody {
    tr {
      td {
        padding: 16px;
        font-size: 14px;
      }

      &:nth-child(even) {
        background: #f9fafb;

        td {
          &:first-child {
            border-radius: 12px 0px 0px 12px;
          }
        }
      }
    }
  }
}

.date-cell {
  color: #6b7280;
}

.badge {
  padding: 6px 11px;
  font-size: 12px;
  border-radius: 10px;

  &-success {
    color: #03543f;
    background: #def7ec;
  }

  &-danger {
    color: #9b1c1c;
    background: #fbd5d5;
  }

  &-info {
    color: #1e429f;
    background: #e1effe;
  }
}

@media (max-width: 768px) {
  table {
    thead {
      tr {
        td {
          &:nth-child(3),
          &:nth-child(4) {
            display: none;
          }
        }
      }
    }

    tbody {
      tr {
        td {
          &:nth-child(3),
          &:nth-child(4) {
            display: none;
          }
        }
      }
    }
  }
}
</style>
