---
layout: default
title: Table Generator
description: make tables for ya classessssss
toc: false
permalink: /tablegenerator
---
<script href="{{site.baseurl}}/assets/js/tablegenerator.js"></script>
<div class="table-generator">
    <div class="text-container">
        <div class="text">
            <b>STUDENTS:</b>
            <i>SELECT A CLASS TO GENERATE FROM</i>
        </div>
        <div class="list"></div>
        <div class="group-numbers">
            <span># OF GROUPS:</span>
            <input id="groupsInput" placeholder="#">
        </div>
        <div class="button">GENERATE TEAMS!</div>
    </div>
    <div class="table-container" id="table-div">
    <!-- Tester tables for styling -->
        <div class="row">
            <div class="table">
                <div class="title">GROUP #1</div>
                <table>
                    <tr>
                        <td>1.</td>
                        <td>person 1</td>
                    </tr>
                    <tr>
                        <td>2.</td>
                        <td>person 2</td>
                    </tr>
                    <tr>
                        <td>3.</td>
                        <td>person 3</td>
                    </tr>
                    <tr>
                        <td>4.</td>
                        <td>person 4</td>
                    </tr>
                </table>
            </div>
            <div class="table">
                <div class="title">GROUP #2</div>
                <table>
                    <tr>
                        <td>1.</td>
                        <td>person 1</td>
                    </tr>
                    <tr>
                        <td>2.</td>
                        <td>person 2</td>
                    </tr>
                    <tr>
                        <td>3.</td>
                        <td>person 3</td>
                    </tr>
                    <tr>
                        <td>4.</td>
                        <td>person 4</td>
                    </tr>
                </table>
            </div>
        </div>
        <div class="row">
            <div class="table">
                <div class="title">GROUP #3</div>
                <table>
                    <tr>
                        <td>1.</td>
                        <td>person 1</td>
                    </tr>
                    <tr>
                        <td>2.</td>
                        <td>person 2</td>
                    </tr>
                    <tr>
                        <td>3.</td>
                        <td>person 3</td>
                    </tr>
                    <tr>
                        <td>4.</td>
                        <td>person 4</td>
                    </tr>
                </table>
            </div>
        </div>
    </div>
</div>