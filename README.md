# learning_git_action


https://github.com/actions/github-script



- No blank space in between
- better use double quotes
- $ is used as @ in c/cpp. Get the value at that variable.


one:
    runs-on: ubuntu-latest
    steps:
        - name: Dump GitHub context
        env:
            GITHUB_CONTEXT: ${{ toJSON(github) }}
        run: echo "$GITHUB_CONTEXT"
        - name: Dump job context
        env:
            JOB_CONTEXT: ${{ toJSON(job) }}
        run: echo "$JOB_CONTEXT"
        - name: Dump steps context
        env:
            STEPS_CONTEXT: ${{ toJSON(steps) }}
        run: echo "$STEPS_CONTEXT"
        - name: Dump runner context
        env:
            RUNNER_CONTEXT: ${{ toJSON(runner) }}
        run: echo "$RUNNER_CONTEXT"
        - name: Dump strategy context
        env:
            STRATEGY_CONTEXT: ${{ toJSON(strategy) }}
        run: echo "$STRATEGY_CONTEXT"
        - name: Dump matrix context
        env:
            MATRIX_CONTEXT: ${{ toJSON(matrix) }}
        run: echo "$MATRIX_CONTEXT"



 - name: get new comment id
        env:
          STP_CONTEXT: ${{ toJSON(steps.pingback.outputs) }}
        run: |
          echo ${{steps.pingback.outputs.result.data}}
          COMMENT_ID=$(echo $STP_CONTEXT | jq '.result | fromjson' | jq .data.id)
          echo $COMMENT_ID
          echo "COMMENT_ID=$COMMENT_ID" >> $GITHUB_ENV